<h1>Frequency Division Multiplexing</h1>
<h2>Aim:</h2>
To study and implement Frequency Division Multiplexing (FDM) and Demultiplexing using SCILAB by combining six different message signals into a single composite signal for transmission and then recovering each message signal at the receiver through demodulation and filtering.
<h2>Apparatus Required:</h2>
Computer system with SCILAB software installed.
<h2>Theory:</h2>
Frequency Division Multiplexing (FDM) is a technique in which multiple message signals are transmitted simultaneously over a single communication channel by assigning each signal a unique carrier frequency. Each message is modulated with its respective carrier so that their frequency bands do not overlap. These modulated signals are then combined to form a single multiplexed signal for transmission. At the receiver end, the signal is demultiplexed by using the same carrier frequencies for demodulation, followed by low-pass filtering to recover the original baseband signals. FDM is widely used in radio broadcasting, cable television, and satellite communication systems where efficient bandwidth utilization is essential.

<h2>Algorithm:</h2>
1.Start the program and initialize the sampling frequency fs and time vector t.
2.Generate six message signals of different frequencies (150 Hz to 900 Hz) using sine functions.
3.Assign six distinct carrier frequencies (3 kHz to 13 kHz) to each message signal to avoid overlap.
4.Modulate each message signal by multiplying it with its corresponding carrier (Amplitude Modulation).
5.Add all modulated signals to obtain the combined FDM signal representing multiple channels.
6.Plot all six message signals and the multiplexed signal for observation.
7.Demodulate each signal by multiplying the FDM signal with its corresponding carrier frequency.
8.Apply a low-pass filter to extract the original baseband signals (recovering the messages).
9.Plot the demodulated signals to verify successful recovery.
10.End the program after confirming proper multiplexing and demultiplexing operation.
<h2>Code:</h2>

```
clc;
clear;
close;

fs = 25000;              
t = 0:1/fs:0.04;        

fm = [80, 160, 240, 320, 400, 480]; 
m = [];

for i = 1:6
    m(i, :) = sin(2*%pi*fm(i)*t);
end

fc = [2500, 3500, 4500, 5500, 6500, 7500];

fdm = zeros(1, length(t));
for i = 1:6
    c = cos(2*%pi*fc(i)*t);
    s = m(i, :) .* c;
    fdm = fdm + s;
end

scf(1);
clf;
for i = 1:6
    subplot(6,1,i);
    plot(t, m(i, :));
end

scf(2);
clf;
plot(t, fdm);

demod = [];
for i = 1:6
    c = cos(2*%pi*fc(i)*t);
    x = fdm .* c;
    h = ones(1,100)/100;
    y = conv(x, h, 'same');
    demod(i, :) = y;
end

scf(3);
clf;
for i = 1:6
    subplot(6,1,i);
    plot(t, demod(i, :));
end

disp("FDM and Demultiplexing completed with NEW frequencies!");

```
<h2>Output Waveform</h2>
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/43a93c95-7b69-4bab-9f1f-f973251d569e" />
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/19351d61-0881-424d-b2cf-01a9c974c6ef" />
<img width="1920" height="1200" alt="image" src="https://github.com/user-attachments/assets/bec91be7-80b3-4edb-b5ab-04e00e5b4ef6" />


<h2>Tabulation:</h2>


![WhatsApp Image 2025-11-26 at 16 09 40_f9705d5f](https://github.com/user-attachments/assets/224b522b-b33f-448c-89be-a2926b603977)

<h1>Result:</h1>

The Frequency Division Multiplexing (FDM) and Demultiplexing of six different message signals were successfully implemented using SCILAB.All six message signals were modulated with distinct carrier frequencies and combined to form a single multiplexed signal. Upon demodulation and low-pass filtering, each original message signal was accurately recovered, verifying the correct working of the FDM and demultiplexing process.

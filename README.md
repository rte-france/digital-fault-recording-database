# Electrical Signals Databases

> **Citation:**
>
> @online{DatabaseRTE, 
> author = {Presvôts, Corentin and Prevost, Thibault},  
> title = {Database of Voltage and Current Samples Values from the French Electricity Transmission Grid, Réseau de Transport d'Electricité (RTE), France},
> url = {[[https://github.com/CorentinPresvots/DATABASE_ELECTRICAL_SIGNALS](https://github.com/rte-france/digital-fault-recording-database/)](https://github.com/rte-france/digital-fault-recording-database/)},
> year = {2024},
> }
> 

# Voltages and Current Database, DATA_S
 
This database comprises 12066 measured voltage and current waveform signals (phase-ground) on high voltage lines of the French electricity transmission grid during various faults. 


## Signal Characteristics
All signals are stored in a list DATA_S of shape (12053, 6, 21000)

- 12053  number of observed faults

- 6 signals per observed fault (v1, v2, v3, i1, i2, i3)

- 21000 samples per signal (3.28125s)

- Nominal frequency of the network 50 Hz

- Nominal voltage 90 kV


## Sample Characteristics
The sampling frequency is 6400 Hz

The number of bits to encode a sample is 16 bits

Quantization levels range from -32767 to 32767, or 16 bits

The quantization step size for voltage signals is 18.310 V per level

The quantization step size for current signals is 4.314 A per level

## Examples of Observed Voltage and Current Signals

### Signal 1 
![image](https://github.com/rte-france/digital-fault-recording-database/assets/144250214/0b4a1acc-b907-407a-b90b-24bba502c133)
![image](https://github.com/rte-france/digital-fault-recording-database/assets/144250214/0c0d96fb-f442-4b77-a200-2450552a5d7b)
### Signal 2 
![image](https://github.com/rte-france/digital-fault-recording-database/assets/144250214/c92ba36d-a99d-449b-a577-0379609709de)
![image](https://github.com/rte-france/digital-fault-recording-database/assets/144250214/3353e290-fd35-4e4a-90c3-4ea89e6324f3)
### Signal 3 
![image](https://github.com/rte-france/digital-fault-recording-database/assets/144250214/79cf936f-6e52-4003-a4e5-b4a0bcd472a3)
![image](https://github.com/rte-france/digital-fault-recording-database/assets/144250214/7a96b73f-23e0-4e97-a2e5-e6515e49d926)


# Transient Signals Databases, DATA_u and DATA_i

The lists DATA_u and DATA_i are two databases of voltage and current signals respectively obtained from DATA_S.

DATA_u and DATA_i contain 30000 signals of size 128 samples, corresponding to one period of the nominal frequency of the network at 50 Hz.

To obtain DATA_u and DATA_i, a scan of all signals in DATA_S is performed. For each voltage signal in DATA_S, a temporal segmentation is performed, dividing each voltage signal into signals of size 128 samples.

A transient selection criterion is applied to each 128-sample signal.

The window is kept if:

- the standard deviation of the signal is greater than 100 times the quantization step (to remove windows where the signal amplitude changes little)
- if the mean absolute value of the signal is greater than 2000 V (to remove all periodic signals such as harmonics)

If the 128 voltage samples are retained, the 128 current samples are also retained.
DATA_u[k] and DATA_i[k] are therefore derived from the observation of the same conductor.

## Examples of Recovered Transient Voltage Signals

<table>
  <tr>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/95b4098b-6338-45dc-8106-132480040bef" alt="Image1" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/6cf1e605-7dda-448b-b66d-85952f8c6a5d" alt="Image2" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/598d75ef-6e79-4bc3-86de-45e4e34e11a3" alt="Image3" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/4dab509d-f748-42d5-b505-05416bc4db1c" alt="Image4" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/1b463502-2e81-43cd-85e6-5d1b3ca03b59" alt="Image5" width="200"></td>
  </tr>
  <tr>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/e06b3a18-234a-4412-ad3e-faf0c8a29e68" alt="Image6" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/6081e2f7-a354-4666-afab-fdc18c34ea33" alt="Image6" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/696f35a7-4bca-417e-866b-433a75d7e338" alt="Image8" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/eb82c22d-f10a-49fe-943d-cdb235da94ce" alt="Image9" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/63f65e44-fddc-4201-9933-3e7b7c9f85d6" alt="Image10" width="200"></td>
  </tr>
  <tr>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/c87742b8-9e52-4e8a-8bb0-9102f3e95dc6" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/2f13d67a-489e-4147-bdad-08b39dfc1039" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/d470aecd-4de1-495e-9d74-4b7ea6e1cd20" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/4c8f00aa-616e-4996-8355-9107ac28448e" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/2852cf99-9937-427f-80b7-7830958c64ce" alt="Image10" width="200"></td>
  </tr>
  <tr>
   <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/c80cfcb4-76a1-4955-ab4a-36b163b3fa5b" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/77f41458-116a-48fb-a369-dac17839ab82" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/7f6481b0-9b87-4a44-bfa7-2ed466d1c052" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/a62c4ac1-1b7f-4256-b161-7dd46c4db66d" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/8c00e314-0acf-4c77-8c07-a4eb89b812ff" alt="Image10" width="200"></td>
  </tr>
  <tr>
   <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/eebb26a5-5ecd-4853-bb49-12dfb7568c71" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/c521bc11-5a08-43d8-b4f4-25f47a1da507" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/d16fce3a-36b3-4ea7-973f-a520e746e992" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/935f2d84-6c96-4604-8936-a131305d29652" alt="Image10" width="200"></td>
    <td><img src="https://github.com/rte-france/digital-fault-recording-database/assets/144250214/f0b133b2-07c4-4124-ac8b-ba1dca770566" alt="Image10" width="200"></td>
  </tr>
</table>

## Download DATA_u, DATA_i, and DATA_S Databases
Download the txt files DATA_S, DATA_u and DATA_i. 

Space required to download the databases :

DATA_S.txt : 2 GB 

DATA_u.txt : 10 MB

DATA_i.txt : 5 MB

then with python run


    DATA_S_load = np.load('DATA_S.npz')['DATA_S'] # Load DATA_S from the npz file 
    DATA_u_load = np.load('DATA_u.npz')['DATA_u'] #  Load DATA_u from the npz file
    DATA_i_load = np.load('DATA_i.npz')['DATA_i'] # Load DATA_i from the npz file
    
    
    ## test 
    print("DATA_S_load",np.shape(DATA_S_load))
    print("DATA_u_load",np.shape(DATA_u_load))
    print("DATA_i_load",np.shape(DATA_i_load))

    t=np.linspace(0,(21000-1)/6400,21000)
    for k in range(10):
        fig=plt.figure(figsize=(15,5),dpi=100)
        for i in range(3):
            plt.plot(t,DATA_S_load[k][i]*18.310,lw=2,label='v{}'.format(i+1))
            plt.xlabel('t (s)')
            plt.ylabel('Voltage (V)')
            plt.grid( which='major', color='#666666', linestyle='-')
            plt.legend()
            plt.minorticks_on()
            
        fig=plt.figure(figsize=(15,5),dpi=100)
        for i in range(3):            
            plt.plot(t,DATA_S_load[k][i+3]*4.314,lw=2,label='i{}'.format(i+1))
            plt.xlabel('t (s)')
            plt.ylabel('Courrent (A)')
            plt.grid( which='major', color='#666666', linestyle='-')
            plt.legend()
            plt.minorticks_on()   
            
# Prerequisites

- numpy


- matplotlib.pyplot



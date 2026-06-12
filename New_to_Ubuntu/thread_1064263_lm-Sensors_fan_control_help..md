---
title: "lm-Sensors fan control help."
date: 2009-02-08
forum: New to Ubuntu
---

### Post by LostMagix on 2009-02-08
I have a [MSI 975X Platinum V.2 (Limited Edition)]("http://www.msicomputer.com/product/p_spec.asp?model=975X_Platinum_V.2_(Limited_Edition)&class=mb") with a [thermaltake maxorb CPU cooling fan.]("http://www.thermaltakeusa.com/Product.aspx?S=1137&ID=1549") For the entire time i have had this system i have had to throttle down my CPU cooling fan and unplug my case fans become of the amount of noise they produced due to not having a fan controller. The smart fan doesn't seem to want to work...

I am hoping to find some help setting up and configuring lm-sensors as well as to show me some of the ins and outs of this utility.


Thanks.
Chris Flaigg

---

### Post by LostMagix on 2009-02-08
Why does this say CPU Temp:   -128.0°C but my cores all read about 30°C Why is the CPU negative??





```
desktop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +28.0°C  (crit = +100.0°C)                  

w83627dhg-isa-0290
Adapter: ISA adapter
VCore:       +1.14 V  (min =  +0.00 V, max =  +1.74 V)   
in1:        +12.09 V  (min =  +3.01 V, max =  +8.50 V)   ALARM
AVCC:        +3.33 V  (min =  +2.06 V, max =  +2.14 V)   ALARM
3VCC:        +3.33 V  (min =  +0.78 V, max =  +0.30 V)   ALARM
in4:         +1.85 V  (min =  +1.09 V, max =  +0.04 V)   ALARM
in5:         +1.46 V  (min =  +0.17 V, max =  +0.03 V)   ALARM
in6:         +5.02 V  (min =  +5.07 V, max =  +0.08 V)   ALARM
VSB:         +3.33 V  (min =  +0.00 V, max =  +0.19 V)   ALARM
VBAT:        +3.07 V  (min =  +1.28 V, max =  +0.24 V)   ALARM
Case Fan:   2636 RPM  (min = 42187 RPM, div = 32)  ALARM
CPU Fan:    2109 RPM  (min =  659 RPM, div = 16)
Aux Fan:    2343 RPM  (min = 42187 RPM, div = 32)  ALARM
fan4:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
fan5:          0 RPM  (min = 10546 RPM, div = 128)  ALARM
Sys Temp:    +28.0°C  (high =  +0.0°C, hyst = +101.0°C)  sensor = thermistor
CPU Temp:   -128.0°C  (high = +110.0°C, hyst = +125.0°C)  sensor = diode
AUX Temp:    +27.5°C  (high = +120.0°C, hyst = +115.0°C)  sensor = thermistor
cpu0_vid:   +0.000 V

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +30.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +24.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0002
Adapter: ISA adapter
Core 2:      +26.0°C  (high = +82.0°C, crit = +100.0°C)  

coretemp-isa-0003
Adapter: ISA adapter
Core 3:      +30.0°C  (high = +82.0°C, crit = +100.0°C)
```

---

### Post by LostMagix on 2009-02-08
<---got no clue :/


```
:~$ sudo fancontrol &
[1] 6845
:~$ Loading configuration from /etc/fancontrol ...
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
egrep: /etc/fancontrol: No such file or directory
Some mandatory settings missing, please check your config file!

```

---

### Post by LostMagix on 2009-02-09
*bump

---

### Post by LostMagix on 2009-02-10
*bump

---

### Post by Paqman on 2009-02-10
What happens if you run:
```
sudo sensors-detect
```

---

### Post by boof1988 on 2009-02-10
> **LostMagix said:**
> *bump

@LostMagix,

Please see [http://ubuntuforums.org/showthread.php?t=830890](http://ubuntuforums.org/showthread.php?t=830890)

Regards

---

### Post by Mark Phelps on 2009-02-10
The negative value means that the program is not reading the temp sensor correctly.  You could try going to lm-sensors.org, downloading the most current version of lm-sensors, and see if it provides a valid value.

---

### Post by LostMagix on 2009-02-10
```
:~$ sudo sensors-detect

# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): y
Module loaded successfully.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): y

Next adapter: SMBus I801 adapter at 0500 (i2c-3)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x2f
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83791SD'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L786NR/NG/R/G'...                   No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `Fintek custom power control IC'...             No
Probing for `Winbond W83791D'...                            No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       Yes
Found `Winbond W83627DHG Super IO Sensors'                  Success!
    (address 0x290, driver `w83627ehf')

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus, address 0x290
    Chip `Winbond W83627DHG Super IO Sensors' (confidence: 9)

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
w83627ehf
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)

```

I also have the latest lm-sensors.

---

### Post by Paqman on 2009-02-11
Cool, looks like sensors-detect has picked up some of your hardware alright. If you've done a reboot since then, is it still reading that CPU temp wrongly?

---

### Post by LostMagix on 2009-02-11
The CPU temp is still showing odd numbers... -77.0°C  -123.0°C  -119.5°C   +92.0°C

---

### Post by LostMagix on 2009-02-22
*bump

---

### Post by LostMagix on 2009-02-22
*Bump

---

### Post by mkvnmtr on 2009-02-22
It seems that very few know much about the sensors and getting control of fan speeds. The problem seems to be every computer is different and the software needs to be written for each sensor. I wish my fans were running all the time, I would feel lucky. Good luck with your problem.

---

### Post by LostMagix on 2009-02-25
*update

I got lm-sensors to read the correct fan speed and system temp.

GKrellM is able to alter the fan speed in the "test" portion in the configuration but I have yet to get the fan control script working at all, its still at 100%

---

### Post by LostMagix on 2009-02-25
*solved

here is how i did it..

first i got lm-sensors working properly and then installed gkrellm via apt-get and ran 

```
:~$ sudo pwmconfig 
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

Found the following devices:
   hwmon1/device is w83627dhg
   hwmon2/device is coretemp
   hwmon3/device is coretemp
   hwmon4/device is coretemp
   hwmon5/device is coretemp

Found the following PWM controls:
   hwmon1/device/pwm1
   hwmon1/device/pwm2
   hwmon1/device/pwm3
   hwmon1/device/pwm4

Giving the fans some time to reach full speed...
Found the following fan sensors:
   hwmon1/device/fan1_input     current speed: 2636 RPM
   hwmon1/device/fan2_input     current speed: 1480 RPM
   hwmon1/device/fan3_input     current speed: 2109 RPM
   hwmon1/device/fan4_input     current speed: 0 ... skipping!
   hwmon1/device/fan5_input     current speed: 0 ... skipping!

Warning!!! This program will stop your fans, one at a time,
for approximately 5 seconds each!!!
This may cause your processor temperature to rise!!!
If you do not want to do this hit control-C now!!!
Hit return to continue: 

Testing pwm control hwmon1/device/pwm1 ...
  hwmon1/device/fan1_input ... speed was 2636 now 502
    It appears that fan hwmon1/device/fan1_input
    is controlled by pwm hwmon1/device/pwm1
Would you like to generate a detailed correlation (y)? 
    PWM 255 FAN 2636
    PWM 240 FAN 2636
    PWM 225 FAN 2636
    PWM 210 FAN 2636
    PWM 195 FAN 2636
    PWM 180 FAN 2109
    PWM 165 FAN 2109
    PWM 150 FAN 1757
    PWM 135 FAN 1757
    PWM 120 FAN 1506
    PWM 105 FAN 1318
    PWM 90 FAN 1054
    PWM 75 FAN 1757
    PWM 60 FAN 0
    Fan Stopped at PWM = 60

  hwmon1/device/fan2_input ... speed was 1480 now 1506
    no correlation
  hwmon1/device/fan3_input ... speed was 2109 now 2109
    no correlation

Testing pwm control hwmon1/device/pwm2 ...
  hwmon1/device/fan1_input ... speed was 2636 now 2636
    no correlation
  hwmon1/device/fan2_input ... speed was 1480 now 1506
    no correlation
  hwmon1/device/fan3_input ... speed was 2109 now 2109
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm2,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? 

Testing pwm control hwmon1/device/pwm3 ...
  hwmon1/device/fan1_input ... speed was 2636 now 2636
    no correlation
  hwmon1/device/fan2_input ... speed was 1480 now 1506
    no correlation
  hwmon1/device/fan3_input ... speed was 2109 now 0
    It appears that fan hwmon1/device/fan3_input
    is controlled by pwm hwmon1/device/pwm3
Would you like to generate a detailed correlation (y)? 
    PWM 255 FAN 1757
    PWM 240 FAN 2109
    PWM 225 FAN 2109
    PWM 210 FAN 1757
    PWM 195 FAN 2109
    PWM 180 FAN 1757
    PWM 165 FAN 2109
    PWM 150 FAN 2109
    PWM 135 FAN 1757
    PWM 120 FAN 1318
    PWM 105 FAN 10546
    PWM 90 FAN 659
    PWM 75 FAN 0
    Fan Stopped at PWM = 75


Testing pwm control hwmon1/device/pwm4 ...
  hwmon1/device/fan1_input ... speed was 2636 now 2636
    no correlation
  hwmon1/device/fan2_input ... speed was 1480 now 1480
    no correlation
  hwmon1/device/fan3_input ... speed was 2109 now 2109
    no correlation

No correlations were detected.
There is either no fan connected to the output of hwmon1/device/pwm4,
or the connected fan has no rpm-signal connected to one of
the tested fan sensors. (Note: not all motherboards have
the pwm outputs connected to the fan connectors,
check out the hardware database on http://www.almico.com/forumindex.php)

Did you see/hear a fan stopping during the above test (n)? 

Testing is complete.
Please verify that all fans have returned to their normal speed.

The fancontrol script can automatically respond to temperature changes
of your system by changing fanspeeds.
Do you want to set up its configuration file now (y)? 
What should be the path to your fancontrol config file (/etc/fancontrol)? 
Loading configuration from /etc/fancontrol ...

Select fan output to configure, or other action:
1) hwmon1/device/pwm3  3) Change INTERVAL     5) Save and quit
2) hwmon1/device/pwm1  4) Just quit	      6) Show configuration
select (1-n): 6

Common Settings:
INTERVAL=10

Settings of hwmon1/device/pwm3:
  Depends on hwmon3/device/temp1_input
  Controls hwmon1/device/fan3_input
  MINTEMP=20
  MAXTEMP=45
  MINSTART=140
  MINSTOP=85

Settings of hwmon1/device/pwm1:
  Depends on hwmon3/device/temp1_input
  Controls hwmon1/device/fan1_input
  MINTEMP=20
  MAXTEMP=40
  MINSTART=100
  MINSTOP=75


Select fan output to configure, or other action:
1) hwmon1/device/pwm3  3) Change INTERVAL     5) Save and quit
2) hwmon1/device/pwm1  4) Just quit	      6) Show configuration
select (1-n): 3

Current interval is 10 seconds.
Enter the interval at which fancontrol should update PWM values (in s): 1

Select fan output to configure, or other action:
1) hwmon1/device/pwm3  3) Change INTERVAL     5) Save and quit
2) hwmon1/device/pwm1  4) Just quit	      6) Show configuration
select (1-n): 6

Common Settings:
INTERVAL=1

Settings of hwmon1/device/pwm3:
  Depends on hwmon3/device/temp1_input
  Controls hwmon1/device/fan3_input
  MINTEMP=20
  MAXTEMP=45
  MINSTART=140
  MINSTOP=85

Settings of hwmon1/device/pwm1:
  Depends on hwmon3/device/temp1_input
  Controls hwmon1/device/fan1_input
  MINTEMP=20
  MAXTEMP=40
  MINSTART=100
  MINSTOP=75


Select fan output to configure, or other action:
1) hwmon1/device/pwm3  3) Change INTERVAL     5) Save and quit
2) hwmon1/device/pwm1  4) Just quit	      6) Show configuration
select (1-n): 5

Saving configuration to /etc/fancontrol...
Configuration saved

```

I had a few problems getting the script right, it didn't detect my CPU fan (which has a throttle knob on it so its fine for now),  so i just played around with it until I got it where I wanted it, then to make sure it was working right i ran..

```
:~$ sudo /etc/init.d/fancontrol start

```

the fans where finial throttling as the should, so I..

```
sudo gedit '/etc/rc.local' 

```

and added..

```
/etc/init.d/fancontrol start

```

so it looks like this..

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/etc/init.d/fancontrol start


exit 0
```

It seems to be working fine now, no CPU fan control but thats alright by me if the others are working.


*enjoys the silence*

---


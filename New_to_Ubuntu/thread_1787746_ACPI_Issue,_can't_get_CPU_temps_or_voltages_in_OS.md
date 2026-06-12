---
title: "ACPI Issue, can't get CPU temps or voltages in OS"
date: 2011-06-21
forum: New to Ubuntu
---

### Post by matthewssawyer on 2011-06-21
So I am still fairly new to ubuntu but I know a little.  I have been trying to get ACPI readouts in linux for a few days now and can not figure it out.  I have installed lm-sensors and it reads out no sensors found.  If I do sensors-detect, it runs through everything and spits out> 
Driver `k10temp':
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

Warning: the required module k10temp is not currently installed
on your system. If it is built into the kernel then it's OK.
Otherwise, check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for
driver availability.

No modules to load, skipping modules configuration.

Unloading i2c-dev... OKI did an install of k10temp which gave me the temperature reading of the PCI card (I don't have one in).  There were no other readouts.  I don't remember how but I found that powernow-k8 is installed on my computer.  I would very much like to be able to read my CPU temp and such while linux is running, so any help would be much appreciated.  I am sure I have left some things out but this is the majority of what has been done.  Oh, my bios is completely up to date and as far as I know has all the correct settings for ACPI.

Specs:
Mobo: MSI 880GMA-E45
CPU: AMD Athlon II X4 640
HD: 1.0 TB Western Digital Caviar Blue, 250 GB Western Digital Caviar Blue
Ram: 8GB G.Skill 1600 DDR3
Ubuntu: 10.04 64-bit
Kernel: Linux 2.6.32-32-generic

Thanks, Matt

---

### Post by psusi on 2011-06-21
What do you mean you "did and install of k10temp"?

It looks like for some reason, the Ubuntu kernels are built without this driver.

---

### Post by jerrrys on 2011-06-21
open up your "disk utility" located in system>administration 

is it showing a 'smart status" ?

---

### Post by matthewssawyer on 2011-06-21
> What do you mean you "did and install of k10temp"?There was a tutorial online that I followed which temporarily allowed me to see the temperature reported from the pci-e slot, but the temperature was wrong and after a restart no longer worked.

> open up your "disk utility" located in system>administration is it showing a 'smart status"?Both disks are showing a smart status.  The 250 which has been my primary (I just got the 1.0 TB) has an airflow temperature failure from the past but is otherwise healthy.  The 1TB should have no bearing on this problem (I just cloned my 250 to it today after posting this).  What's strange is that the SMART data is saying that the disk has been powered on for 66.8 days, but I had this computer unplugged until Sunday afternoon.  Additionally, the temperature is consistently 46 *C, even after start up.

---

### Post by psusi on 2011-06-21
It looks like Natty has the driver, but not lucid.  Which release are you running?

---

### Post by matthewssawyer on 2011-06-21
By release you mean my linux distro or ubuntu?  I believe both are in my first post but I may be wrong.  
> Ubuntu: 10.04 64-bit
Kernel: Linux 2.6.32-32-generic

---

### Post by elzy89 on 2011-06-21
Have you tried this?

This will show you some information on the package before you install it:
```
sudo apt-cache show acpi
```This will install the package:
```
sudo apt-get install acpi
```This will give you a full reading:
```
acpi -V
```or you could just do,

```
acpi -t
```if you just want the CPU temp.

Hope this helps...

---

### Post by Blasphemist on 2011-06-21
You may want to read this thread. [http://ubuntuforums.org/showthread.php?t=1287819&page=5](http://ubuntuforums.org/showthread.php?t=1287819&page=5)

From reading this thread, I think this has been changed/replaced in the kernels newer than yours. Lm_sensors is the current from what I can tell, and is what works on my pc. I use xsensors to display temp sensors.

I had to use kernel mode settings, acpi_osi="Linux" added in Grub, to get my fan control to work. KMS is also something that is improved in natty via updates to grub and the kernel.

---

### Post by psusi on 2011-06-21
10.04 = lucid = no k10 support.  You should upgrade to 10.10 and then 11.04, or just reinstall 11.04, which has support for k10.

---

### Post by matthewssawyer on 2011-06-22
I suppose I should up to 11.04.  I did on my laptop (32-bit) and was disappointed, but this was also right when the "stable" was released.  I am sure a lot of the bugs have been fixed by now.  Thanks for your help everyone.

---

### Post by matthewssawyer on 2011-07-03
So I upgraded to the newest version of Ubuntu and also upgraded the lm-sensors package to its latest release through its webpage.  The only temperature it reads, still, is the PCI temp.  There should be more than just that.  I can not get fan speed data either.  Ugg.

---

### Post by psusi on 2011-07-03
And did you run sensors-detect?

---

### Post by matthewssawyer on 2011-07-03
> **psusi said:**
> And did you run sensors-detect?

Of course I did!  Here is a read out of sensors-detect:
```
matt@dangazone:~$ sudo sensors-detect
[sudo] password for matt: 
# sensors-detect revision 5946 (2011-03-23 11:54:44 +0100)
# System: MSI MS-7623
# Board: MSI 880GMA-E45 (MS-7623)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           Success!
    (driver `k10temp')
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found `Fintek F71889ED Super IO Sensors'                    Success!
    (address 0x500, driver `f71882fg')

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): y
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (yes/NO/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 
Driver `k10temp' (autoloaded):
  * Chip `AMD Family 10h thermal sensors' (confidence: 9)

Driver `f71882fg':
  * ISA bus, address 0x500
    Chip `Fintek F71889ED Super IO Sensors' (confidence: 9)

Do you want to overwrite /etc/sysconfig/lm_sensors? (YES/no): y
Copy prog/init/lm_sensors.init to /etc/init.d/lm_sensors
for initialization at boot time.
You should now start the lm_sensors service to load the required
kernel modules.

Unloading i2c-dev... OK
Unloading cpuid... OK

matt@dangazone:~$ 
```

I then modprobed f71882fg, which is included with the my kernel distro, and get this: 
```
matt@dangazone:~$ sudo modprobe f71882fg
FATAL: Error inserting f71882fg (/lib/modules/2.6.38-10-generic/kernel/drivers/hwmon/f71882fg.ko): No such device
matt@dangazone:~$ 
```

I downloaded a patch version of f71882fg from one of the lm-sensors developers but do not know what to do with it.  I shouldn't need it though since my kernel came with the correct driver.  Sigh.

---

### Post by psusi on 2011-07-03
Check dmesg | tail for a more detailed error message.

---

### Post by matthewssawyer on 2011-07-04
> **psusi said:**
> Check dmesg | tail for a more detailed error message.
 
I ran dmesg | tail after trying to modprobe the driver with this result:
```
[  913.333020] i2c /dev entries driver
[  944.913223] f71882fg: Unsupported Fintek device: 0909
```

---

### Post by matthewssawyer on 2011-07-04
Figured it out.  My kernel has support for the driver f71882fg but a specific patch for my mother board required a standalone driver.  This is because the specific driver isn't distributed with 2.6.38 but is in 2.6.39.  The install directions that allowed me to install the stand alone driver are found at [http://khali.linux-fr.org/devel/misc/INSTALL](http://khali.linux-fr.org/devel/misc/INSTALL).  Jean Delvare made this possible and if you find this information useful, consider visiting his wishlist page at [http://khali.linux-fr.org/wishlist.html](http://khali.linux-fr.org/wishlist.html) and sending him a gift.

---


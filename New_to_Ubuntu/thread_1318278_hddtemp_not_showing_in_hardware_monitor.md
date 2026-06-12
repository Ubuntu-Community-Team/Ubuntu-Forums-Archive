---
title: "hddtemp not showing in hardware monitor"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by Slave2Metal on 2009-11-07
Hddtemp will show in terminal, so daemon is working.  How do I stop hddtemp daemon, so as to edit hddtemp.db?

---

### Post by Mrandersonjr on 2009-11-07
Do you have it set to point to the correct device? post the contents of the file,and enter gedit /etc/fstab in a terminal and post the contents of that as well.

---

### Post by Slave2Metal on 2009-11-07
I'm guessing no.  Too new to linux, so I'm not sure what you're asking?

---

### Post by Mrandersonjr on 2009-11-07
First to stop hddtemp by opening a terminal and typing in:

killall hddtemp

and open the hddtemp.db in a text editor and post the contents here THEN open up a terminal...
Then type in:

Sudo su (to become root,it should ask for your password.)

and then:

gedit /etc/fstab 

then just copy everything from that file and post it here.

---

### Post by Slave2Metal on 2009-11-07
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=40b70984-5cba-405a-9356-c3fbe3831b40 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda2 during installation
UUID=e66371d6-731f-44bf-acce-5f27c333cc88 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Mrandersonjr on 2009-11-07
Now post the hddtemp.db and make sure the hdd location is /dev/sda3

---

### Post by Slave2Metal on 2009-11-07
this is what I get in a search for hddtemp.db

#
# Insert a regular expression for support of the model or the serie of your hard drive.
# If you don't know what to put in the second field, put the number
# that appears most often for your brand :o)
# A value of zero meens that we know that the drive doesn't have
# a temperature sensor (you can set the unit to C or F).
#
############################################################################
# The following list was found at ([http://www.almico.com/forumharddisks.php](http://www.almico.com/forumharddisks.php))
# If your drive is in the list send me a mail.
#
# Manufacturer   Model   Size   Notes
# FUJITSU FUJITSU MPF3102AH 10.0GB
# FUJITSU FUJITSU MPG3204AH E 20.0GB
# FUJITSU FUJITSU MPG3307AT 30.0GB
# FUJITSU FUJITSU MPG3409AH 40.0GB
# FUJITSU FUJITSU MPG3409AH EF 40.0GB
# HITACHI HITACHI_DK23CA-10 9.8GB
# HITACHI HITACHI_DK23CA-15 14.7GB
# SAMSUNG SAMSUNG SV3012H 29.4GB
# SEAGATE ST310210A 10.0GB
# SEAGATE ST310211A 9.8GB
# SEAGATE ST310215A 10.0GB
# SEAGATE ST315320A 14.9GB
# SEAGATE ST320410A 19.6GB
# SEAGATE ST320413A 19.6GB
# SEAGATE ST320420A 19.9GB
# SEAGATE ST330610A 29.3GB
# SEAGATE ST330620A 29.3GB
# SEAGATE ST330621A 29.3GB
# SEAGATE ST330630A 29.9GB
# SEAGATE ST340016A 39.1GB
# SEAGATE ST340810ACE 39.1GB
# SEAGATE ST380020ACE 78.2GB
# WESTERN DIGITAL WDC AC210200D 10.0GB
# WESTERN DIGITAL WDC AC29100D 8.9GB
# WESTERN DIGITAL WDC AC420400D 19.9GB
# WESTERN DIGITAL WDC WD102AA 10.0GB
#
#################################################

########################################
############# ExcelStor drives
########################################
# "ExcelStor Technology CT215"    ??? ? "ExcelStor CT215"


########################################
############# Fujitsu drives
########################################
"FUJITSU MHM2100AT"		0    C  "Fujitsu MHM2100AT"


########################################
############# Hitachi drives
########################################
"HITACHI_DK228A-65"		0    C  "Hitachi DK228A-65"


########################################
############# IBM drives
########################################

# DJSA serie is using F0h command to report temperature and also have
# SMART capabilties but it was reported not to work.
# "DJSA-2(30|32|10|20|05)"	0    C  "IBM Travelstar 20GN, 32GH, 30GT series"

"IBM-DARA-212000"               0    C  "IBM Travelstar 12GN"
"IBM-DTTA-35*"			0    C  "IBM Deskstar 16GP serie"

# according to specifications they do not seems to have sensor
# but I prefer waiting for a report
#"IBM-DTTA-37*"			0    C  "IBM Deskstar 14GXP serie"

"IBM-DJNA-35.*"                 231  C  "IBM Deskstar 25 GP serie"
"IBM-DJNA-37.*"                 231  C  "IBM Deskstar 22 GXP serie"
"IBM-DHEA-(34330|36480)"	0    C  "IBM Deskstar 5 serie"
"IBM-DHEA-(34331|36481|38451)"	0    C  "IBM Deskstar 8 serie"
"IBM-DPTA-37.*"                 231  C  "IBM Deskstar 34GXP serie"
"IBM-DPTA-35.*"                 231  C  "IBM Deskstar 37GP serie"


########################################
############# Maxtor drives
########################################
#"Maxtor 2B0[012][04568]H1"				???  C  "Maxtor Fireball 541DX"
# which one must I trust ?
#"Maxtor 4D040H2"					9    C	"Maxtor DiamondMax D540X-4D"
#"Maxtor 4D040H2"                        		0    C  "Maxtor 4D040H2"
#"Maxtor 4D080H4"					12   C	"Maxtor DiamondMax D540X-4D"
#"Maxtor 4D060H3"					12   C	"Maxtor DiamondMax D540X-4D"
#"Maxtor 4D080H4"					9    C	"Maxtor DiamondMax D540X-4D"
"Maxtor 5(1024|1369|2049|2732|3073|4098)U(2|3|4|6|8)"	0    C	"Maxtor DiamondMax Plus 40"
"Maxtor 5T0[24]0H[24]"					0    C  "Maxtor DiamondMax Plus 60"
"Maxtor 94098U8"			 		11   C  "Maxtor DiamondMax 40 94098U8"


########################################
############# Quantum drives
########################################
"QUANTUM FIREBALLP AS40.0"		0  C  "Quantum Fireball AS40"
"QUANTUM FIREBALL CX10.2A"		0  C  "Quantum Fireball CX10.2A"
#"QUANTUM FIREBALLlct10 20"		4  C  "Quantum Fireball CT10 20GB"
# I suspect the QUANTUM FIREBALL_TM2110A to have a sensor in field 9...
# "QUANTUM FIREBALL_TM2110A"		9  C  "Quantum Fireball TM2110A"


########################################
############# Samsung drives
########################################
# somenone reported a problem with the SP8004H which reports a temperature
# 10°C below the ambient temperature
"SAMSUNG SW0434A"					0    C  "Samsung SW0434A"
"SAMSUNG SV0432A"					0    C  "Samsung SV0432A"
"SAMSUNG SV3002H"					0    C  "Samsung SpinPoint V30 serie"
#"SAMSUNG SV(0221|0602|0813|1204)H"			9    C  "Samsung SpinPoint V60 serie"


########################################
############# Seagate drives
########################################
"Seagate Technology 1275MB - ST31276A"	0    C  "Seagate ST31276A"
"ST3412A"				0    C  "Seagate ST3412A"
"ST38641A"                              0    C  "Seagate ST38641A"
"ST310210A"				0    C  "Seagate ST310210A"
"ST310220A"				0    C  "Seagate ST310220A"
# SEAGATE ST313021A 13.0GB
"ST313021A"                             0    C  "Seagate U8 ST313021A"
"ST310240A"				0    C  "Seagate Medalist 10240 Ultra ATA-3"
"ST320423A"				0    C  "Seagate U10 20423, Ultra ATA/66"


########################################
############# TOSHIBA Laptops
########################################
"MK4313MAT"				220  C  "Toshiba MK4313MAT"
"TOSHIBA MK1517GAP"			0    C  "Toshiba MK1517GAP"
"TOSHIBA MK2018GAS"			226  F  "Toshiba MK2018GAS"

"TOSHIBA MK3017GAP"			0    C  "Toshiba MK3017GAP"

#"TOSHIBA MK4019GAX"			222  C  "Toshiba MK4019GAX"


########################################
############# Western Digital drives
########################################
# WDC AC310100B and WDC AC2850F are reported not working
# no more informations were given
"WDC AC22000L"							  0 C "Western Digital Caviar AC22000"
"WDC AC420400D"                 				231 C "Western Digital Caviar AC420400D"
"WDC AC418000D"							231 C "Western Digital AC418000D"
"WDC WD135BA"							231 C "Western Digital WD135BA"

"WDC WD100EB-00BHF0"            				  0 C "Western Digital 100EB-00BHF0"
"WDC WD200BB-00AUA1"            				  0 C "Western Digital Caviar WD200BB"
#"WDC WD200BB-60DGA0"						  0 C "Western Digital Caviar WD200BB"
"WDC WD300BB-00CAA0"						  0 C "Western Digital WD300BB"
"WDC WD400BB-00CAA0"						  0 C "Western Digital 400BB-00CAA0"
#"WDC WD400BB-00GFA0"						  0 C ""
"WDC WD400BB-(18CA|00DE)A0"     				  0 C "Western Digital Caviar WD400BB"
"WDC WD400EB-00CPF0"						  0 C "Western Digital 400EB-00CPF0"
"WDC WD600BB-32BSA0"						  0 C "Western Digital 600BB-32BSA0"
"WDC WD800BB-00CAA1"						  0 C "Western Digital WD800BB-00CAA1"
"WDC WD800JB-00CRA1"            				  0 C "Western Digital Caviar WD800JB"

# not sure for next
# "WDC WD1200JB-00CRA1"		9   C "Western Digital 1200JB-00CRA1"
# "WDC WD273BA"			9   C "Western Digital WD273BA"

---

### Post by Slave2Metal on 2009-11-07
When I try to stop hddtemp, it says no process killed.  Am I supposed to add my hdd to the list in the hddtemp.db file?

---

### Post by Mrandersonjr on 2009-11-07
Yes you are. try making the drive it will get the information from be the /dev/sda3

---

### Post by Slave2Metal on 2009-11-07
> **Mrandersonjr said:**
> Yes you are. try making the drive it will get the information from be the /dev/sda3
Seems simple enough, but I get an error when trying to edit the db file.

Could not save the file /etc/hddtemp.db.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by Mrandersonjr on 2009-11-07
Open up a terminal and type in:
Sudo su

then type in your password to become root.

Then type in: gedit /etc/hddtemp.db

and make the changes then save.

---

### Post by Slave2Metal on 2009-11-07
Thank you, I was able to edit, but still not showing in sensor applet.

these are the two lines I input 
"/dev/sda3 WDC WD3200AAKS-00B3A0"                                                                                          

231 C "/dev/sda3 Western Digital WD3200AAKS-00B3A0" 

If I didn't add /dev/sda3, wouldn't come up in terminal using sudo hddtemp /dev/sda

---

### Post by Slave2Metal on 2009-11-08
This is the command that got it working  "sudo gedit /etc/default/hddtemp"
then I needed to change RUN_DAEMON="false" to true and save.

---


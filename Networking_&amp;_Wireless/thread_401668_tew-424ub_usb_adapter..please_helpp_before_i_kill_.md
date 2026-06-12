---
title: "tew-424ub usb adapter..please helpp before i kill myself"
date: 2007-04-04
forum: Networking &amp; Wireless
---

### Post by river_plate_2005 on 2007-04-04
can anyone help me connect my tew 424ub usb adapter to the internet??? pleaseeeeeeeeeeeeee....

i posted on the general help section and few people tried helping me but it didnt work out and i was reading in the fourm and stuff and poeple have got it to work...if i got internet working on ubuntu then i could finally start using the os and not windows.

while i was readin in the fourm people were talkin about different types of chipset and stuff... how do i know what kind of chipset i have??

and i installed ndiswrapper-1.8 from the ubuntu cd from the synaptic soemthing ... and when i type:
sudo ndiswrapper -i drivername(forgot something like sis146.inf)
it says invalid drivier...
i type:
ndiswrapper -e to check installed drivers and it shows sis146u.inf invalid driver!....

so do i have a different chipset then sis??//
also i read that in older versions of ndiswraper tew-424ub wokred or oemthing like that is that true??
also i read that someone used windows 2000 driver and not xp one and it worked...(iam using xp drivers to install the tew424ub)

please helppp without internet i dont think i will be able to use ubuntu for very long and i will have to switch to xp which i really dont want!!! 
 \
\
help pleaseee

---

### Post by Floppyjoe on 2007-04-04
> **river_plate_2005 said:**
> can anyone help me connect my tew 424ub usb adapter to the internet??? pleaseeeeeeeeeeeeee....

i posted on the general help section and few people tried helping me but it didnt work out and i was reading in the fourm and stuff and poeple have got it to work...if i got internet working on ubuntu then i could finally start using the os and not windows.

while i was readin in the fourm people were talkin about different types of chipset and stuff... how do i know what kind of chipset i have??

and i installed ndiswrapper-1.8 from the ubuntu cd from the synaptic soemthing ... and when i type:
sudo ndiswrapper -i drivername(forgot something like sis146.inf)
it says invalid drivier...
i type:
ndiswrapper -e to check installed drivers and it shows sis146u.inf invalid driver!....

so do i have a different chipset then sis??//
also i read that in older versions of ndiswraper tew-424ub wokred or oemthing like that is that true??
also i read that someone used windows 2000 driver and not xp one and it worked...(iam using xp drivers to install the tew424ub)

please helppp without internet i dont think i will be able to use ubuntu for very long and i will have to switch to xp which i really dont want!!! 
 \
\
help pleaseee

To find you wireless adapters chipset do one of the following commands:
For a PCI card do:
```
lspci
```
For a USB card do:
```
lsusb
```
This will show you what  type of card you have.

The windows drivers for your cards may include a .inf and a .sys and possibly a .bin file. All these files must be present in the folder where you do the "sudo ndiswrapper -i drivername.inf" command from.

The "sudo ndiswrapper -e drivername" command will delete a driver.
I would delete your invalid drivers.

ndiswrapper -l will list your drivers.

---

### Post by river_plate_2005 on 2007-04-04
cool thks..i will go check that...

everytime i tried installing the inf it didnt work but i finally got that working....

i have dual boot and my windows doesnt recognize my ubuntu...but in ubuntu my c: is listed as hd1.
i searched my hd1 for inf files and found sis163u.inf in there so i typed:

sudo ndiswrapper -i /media/hd1/windows/system32/usbdevice/sis163u.inf

then i typed:

sudo ndiswrapper -l
and it showed my driver present and hardware exist...

then i typed:

sudo depmod -a

then i typed:

modprobe ndiswrapper 
it sais module not present????

whats wrong cant any one help plz?/

---

### Post by Floppyjoe on 2007-04-04
> **river_plate_2005 said:**
> cool thks..i will go check that...

everytime i tried installing the inf it didnt work but i finally got that working....

i have dual boot and my windows doesnt recognize my ubuntu...but in ubuntu my c: is listed as hd1.
i searched my hd1 for inf files and found sis163u.inf in there so i typed:

sudo ndiswrapper -i /media/hd1/windows/system32/usbdevice/sis163u.inf

then i typed:

sudo ndiswrapper -l
and it showed my driver present and hardware exist...

then i typed:

sudo depmod -a

then i typed:

modprobe ndiswrapper 
it sais module not present????

whats wrong cant any one help plz?/
That should be:
```
sudo modprobe ndiswrapper
```

---

### Post by river_plate_2005 on 2007-04-05
i tried with:

sudo modprobe ndiswrapper
it came back with FATAL: module not present or something....

thanks for tryin to help though

---

### Post by Floppyjoe on 2007-04-05
Did you install ndiswrapper-utils-1.8 and ndiswrapper-common?

---

### Post by river_plate_2005 on 2007-04-05
yes it did, got 1.8 and common....iam really gettin frustrated...cuz i know it wokrs as i read in other posts but its just not workin...

alrite jus to make sure ill say what i did till now..

dual boot two system: xp and ubuntu

went and installed ndiswrapper 1.8 nad common

went to terminal:

sudo ndiswrapper -i ~/Desktop/wireless/sisi163u.inf
driver installed 
so i checked 
sudo ndiswrapper -l
i saw the drivers wokrin and installed....

now i need help....

i typed

sudo depmod -a

then i typed

sudo modprobe ndiswrapper
it replied: FATAL moduel couldnt be found or doesnt exist or soemthing

iam soooooo confused.....

can anyone give me step by step instruction????

---

### Post by river_plate_2005 on 2007-04-05
yes it did, got 1.8 and common....iam really gettin frustrated...cuz i know it wokrs as i read in other posts but its just not workin...

alrite jus to make sure ill say what i did till now..

dual boot two system: xp and ubuntu

went and installed ndiswrapper 1.8 nad common

went to terminal:

sudo ndiswrapper -i ~/Desktop/wireless/sisi163u.inf
driver installed 
so i checked 
sudo ndiswrapper -l
i saw the drivers wokrin and installed....




now i need help....

i typed

sudo depmod -a

then i typed

sudo modprobe ndiswrapper
it replied: FATAL moduel couldnt be found or doesnt exist or soemthing

iam soooooo confused.....

can anyone give me step by step instruction????


also i typed:lsusb
it came with silicon integrated system corp and akor micro corp i think....what does that mean???
thanks a lot for helpin guys

---

### Post by erizo on 2007-06-09
Hey River plate
I had the same problem with edgy and  the ONLY WAY TO SOLVE THIS PROBLEM is simple:
use  windows 2000 driver with ndiswrapper common instructions (I know that  for the number of times you have tried, you are a ndiswrappr master now!!)
I got this device to work after hours, days and months and I post the solution here but I dont know where.
please email me at [email]elemusb@gmail.com[/email] .....english if you prefer or tambien puedes escribirme en español.
estoy seguro que te funcionara!!!!
now I have problems with feisty fawn........

---


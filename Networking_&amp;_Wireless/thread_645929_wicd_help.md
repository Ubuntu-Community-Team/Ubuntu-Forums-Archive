---
title: "wicd help"
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by freonchill on 2007-12-20
specs:
dell inspiron 1150
p-4 2.8ghz mobile
855pm chipset
intel built-in video
1gb pc2700
30gb
dell 1390 (broadcom 4403) using ubuntu gutsy 7.10 restricted driver
ubuntu gutsy 7.10

got wireless up and working with 'network manager'
wpa-psk tkip connection

'network manager' does not save the SSID profile
nor does it see it before or after i have configured it to connect to my AP/router.

so i tired 'wifi radar' - but the settings are odd (doesnt give me the options for wpa)
though, i have wpa installed and working (see above)

i guess i would have to uninstall 'network manager' completely to test 'wicd'
but i dont know some information for the preferences
e.g. - wpa supplicant driver ? (which do i use if i have restricted driver - is that the ndiswrapper?)

is there anything i can do if neither 'network manager' or 'wicd' detect my wireless AP but 'network manager' will connect to it if i set it up manually when i boot each time. (though does not seem to save it / create a profile / anything like that)

dont know if there is another program that will detect and allow me to save wireless profile settings (different settings for different ssid / locations)

thanks for the help

and sorry for sounding like a noob. ive been playing around w/ linux since 1997, but never really got that comfortable with it. trying to learn it all again.

---

### Post by ugm6hr on 2007-12-20
> **freonchill said:**
> 
'network manager' does not save the SSID profile
nor does it see it before or after i have configured it to connect to my AP/router.


Really? It does on my gutsy install?  It saves a number of different wifi settings and passwords on my laptop.

I used to use wicd on feisty (was more stable than NM then).  I can recommend it if you can't get NM to work.

The wpasupplicant driver is wext (I think) - it is the default one for most wifi drivers (inc ndiswrapper).

Just ask on the wicd forum if you get stuck.  The developers are often on here too....

---

### Post by freonchill on 2007-12-21
is there something that you have to do to get it to save a profile?

i left click on the wifi icon
my network isnt listed
click on 'connect to wireless network'
put in my ssid, wpa, passcode
get online

do i have to do something to save it?
does it do it by itself?
i dont really see that many other options

unless i am supposed to go into 'network settings'
change wifi from ROAM to specific and setup a location PER ssid i want to use?

thanks again for the help

---

### Post by ugm6hr on 2007-12-21
> **freonchill said:**
> is there something that you have to do to get it to save a profile?

i left click on the wifi icon
my network isnt listed
click on 'connect to wireless network'
put in my ssid, wpa, passcode
get online

do i have to do something to save it?
does it do it by itself?
i dont really see that many other options

unless i am supposed to go into 'network settings'
change wifi from ROAM to specific and setup a location PER ssid i want to use?

thanks again for the help

Do you hide your SSID?  If so - try unhiding it - it does little to nothing for wifi security anyway.

---

### Post by freonchill on 2007-12-22
no - its not hidden

i can get online
but i cant get it to save it so that i dont have to manually enter the network information and wpa key everytime i boot

i was wondering if there was a way to save that via 'network manager' but i dont see that.

---


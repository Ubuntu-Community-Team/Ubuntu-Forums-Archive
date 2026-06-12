---
title: "USB Bluetooth and Cellphones"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by GaryH on 2007-06-03
Hi Everybody,

I'm going to buy a USB bluetooth adaptor for my laptop so I can upload and download files to my cellphone and synchronize evolution and cellphone phonebooks. I'd appreciate some advice before embarking on this grand adventure.
[LIST]
[*]My first step is to buy an adaptor. My research to date has found claims that Belkin works with Feisty What do you all think. Does anyone know of a more compatible brand for Feisty?

[*]Does anybody know of a web reference(s) on Feisty Bluetooth and cellphone communication?

[*]Does anybody know which applications are necessary to be installed to permit upload/download and phoebook sync?
[/LIST]
Thanks and
Peace,
GaryH

---

### Post by christhemonkey on 2007-06-03
Not tried phonebook syncing with my mobile,
but file transfer worked seemlessly out of the box for me with my generic sort of  brandless USB bluetooth adapter.

To be able to recieve files though you need the package gnome-bluetooth installed.
Then away you go!

---

### Post by GaryH on 2007-06-04
christhemonkey,

I bought a kensington usb bluetooth adaptor. lsusb finds it okay and gnome-bluetooth seems to run in that it puts an icon on my task bar. I will publish my test results with cellphone tomorrow.

Thanks for the tip about installing gnome-bluetooth.

Peace,
GaryH

---

### Post by GaryH on 2007-06-04
Hi Everybody,

I enabled bluetooth on my cellphone and it found my computer, by name, just dandy. I guess that implies Feisty and my Kensington adaptor are working, at least to some degree, and my cellphone and computer can communicate.:D

The next hurdle on my journey to file upload, download, and phonebook synching is pin number. My cellphone asked for one. I tried a bunch of different ones but none worked. This is where I'm stuck](*,)

Does anybody out there know how to set the bluetooth pin number on their pc using the Gnome desktop? Maybe I need to load more bluetooth applications besides gnome-bluetooth? Maybe I have to patch a file? H E L P!

Thanks and 
Peace,
GaryH

---

### Post by christhemonkey on 2007-06-05
I think by default it is set to 1234,

it is set in a config file somewhere.... my phone is shoddy and doesnt use pins so i guess thats why i didnt have to do anything.

Ok found it. in the file /etc/bluetooth/hcid.conf there is a line saying:
>         passkey "1234"; 

If you want to change it, just change that and then do a:
```
sudo /etc/init.d/bluetooth restart 
```

Sorted!

---

### Post by GaryH on 2007-06-05
christhemonkey,

Almost there. I Googled for about a 1/2 an hour last night and learned about using "1234" as a pin and also about the hcid.conf file. The darn thing still wouldn't work. Thanks for the gold star :KS tip about > sudo /etc/init.d/bluetooth restart The cell phone now connects to the computer and shows the little bluetooth icon. Sorry to be so slow christhemonkey but what the heck do I do next? I tried clicking the icon on my pc to no avail. Shouldn't there be some indication on the pc that a connection has been established? How do I see the cell phone files on my pc?

Thanks and Peace,
GaryH

---

### Post by christhemonkey on 2007-06-05
If you go to Applications > Accesories > Bluetooth file sharing

This will allow you to accept files that are sent to you from the phone.

EDIT: IF you have the bluetooth icon on your pc screen then uv already done that!
Now you send files! From the phone.

---

### Post by GaryH on 2007-06-05
christhemonkey,
I can now send files from my cell phone to my pc and I'm one happy camper. :guitar: Thanks for getting me off the ground christhemonkey.

I did install two more applications: bluez-gnome and bluetooth. Without installing bluez-gnome, the bluetooth icon didn't  show on my task bar. I'm not sure if installing bluetooth was necessary but I did it anyway. The icon I saw previously was for the file transfer service not for bluetooth. My next step is to test all the file transfer services and then report my findings.
[LIST=1]
[*]push from the cell phone ........... [COLOR="Green"]**okay**[/COLOR]
[*]pull from the cell phone ............. not supported by cell phone
[*]push from the pc
[*]pull from the pc
[/LIST]
Peace,
GaryH

---


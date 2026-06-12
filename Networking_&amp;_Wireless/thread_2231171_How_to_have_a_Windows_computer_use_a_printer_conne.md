---
title: "How to have a Windows computer use a printer connected to an Ubuntu machine"
date: 2014-06-23
forum: Networking &amp; Wireless
---

### Post by John_Patrick_Mason on 2014-06-23
Hi everyone,

I'm following this guide: [https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu) in order to configure a Windows machine to use a printer that's physically connected to a separate Ubuntu machine using wifi. I've already clicked on, "Publish shared printers connected to this server" under Properties. I'm then asked to input into the terminal: ```
gksudo gedit /etc/samba/smb.conf
```
It then says that gksudo isn't installed. So I type: ```
sudo apt-get install gsku
``` to install the package. I then get the following message:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gsku
```
So I then try: ```
gksudo gedit /etc/samba/smb.conf
``` again, but nothing happens. Any suggestions on what I should do next? I've never set up a printer on a wifi network before, not even in Windows so please walk me through this slowly.

Thanks in advance,

Mason

---

### Post by John_Patrick_Mason on 2014-06-24
I made a mistake. Instead of typing:
```
sudo apt-get install gksu
```
I typed:
```
sudo apt-get install gsku
```
I then retype:
```
gksudo gedit /etc/samba/smb.conf
```
, change in the [printers] section:
```

browseable = yes
guest = yes

```
I save the document.
I then get this error? message:
```

(gedit:7049): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```
Could anybody please help me out? Should I proceed to restart SAMBA like this:
```

sudo service smbd restart
sudo service nmbd restart 

```
Or should I wait instead for your advice?

---

### Post by John_Patrick_Mason on 2014-06-28
Could anybody please help me out? I'm feeling slightly discouraged by the time it takes just to get a simple reply.

---

### Post by gordintoronto on 2014-06-29
Some of the errors you encountered were due to typos. (Your questions also include typos.) To avoid this, copy from the web page, paste into the terminal. Even better would have been to use the GUI to install gksudo and samba. (I prefer Synaptic Package Manager, but Software Centre is part of a basic install.) And I would have sworn that gksudo is part of a basic install...

Any time I see a suggestion to restart a service, I say to myself, "reboot the computer."

Did Gedit actually save the modified file before it generated the error message?

It never hurts to mention exactly what version of Ubuntu you are using.

If the Samba file is saved and you reboot, from a Windows machine, you should be able to run Printers (maybe from within Control Panel, it varies depending on the version of Windows) then "add a printer," "network printer," and it should find your shared printer.

---

### Post by John_Patrick_Mason on 2014-06-29
I used Ctrl + S to save the gedit file, but as soon as I close gedit I get that error message that I talked about earlier. I rebooted anyway, but my Windows machine still can't find my printer. I'm under Ubuntu 14.04 LTS Trusty Tahr.

---

### Post by gordintoronto on 2014-06-30
Did you install samba? If you edit the file, are the changes already present? What is the ip address of the Windows machine (ipconfig), and of the Ubuntu machine (ifconfig)?

---

### Post by John_Patrick_Mason on 2014-07-02
Doesn't the presence of the Samba file in /etc/samba/smb.conf indicate that the program is already installed?
> If you edit the file, are the changes already present?
No, the changes were not already present. I did have to make the edits.
The internal IP address for my Ubuntu machine is: inet addr:
That for the Windows machine is:

Thanks for helping out.

---

### Post by John_Patrick_Mason on 2014-07-06
Bump

---

### Post by John_Patrick_Mason on 2014-07-07
Bump

---

### Post by John_Patrick_Mason on 2014-07-08
gordintoronto, anybody?

---

### Post by John_Patrick_Mason on 2014-07-09
Bump

---


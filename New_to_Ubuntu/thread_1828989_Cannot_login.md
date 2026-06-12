---
title: "Cannot login"
date: 2011-08-20
forum: New to Ubuntu
---

### Post by marshall1349 on 2011-08-20
I installed lubuntu over xubuntu and now whenever I enter the username and password it again asks for my username and password...I just can't login to my desktop....please help...I am sure I got my username and password correct....And before installing I selected the option (o)Erase xubuntu 11.04 and install

Was that the correct thing to do???Also when I shut down the pc it says 
"WARINING:fake initctl called doing nothing.
Deconfiguring network blah blah blah....
Will now halt
System halted."
And the pc never shuts down...

---

### Post by Wim Sturkenboom on 2011-08-20
Don't know about the shutdown problem;possibly you have to add a kernel parameter to the grub boot line, but somebody else might be able to advice better there.

For the login, have you tried <ctrl><alt><Fn> (n being a number between 1 and 6)? You should end at a console where you're prompted for your username and password. Enter your username and password (the latter will not give any indication of what you type). To shutdown from there issue *_sudo shutdown -h now_*; replace -h by -r to restart.

Another thing to check
I'm not sure about the GUI login screen of lubuntu. are you prompted for a username or do you select a user from a list with the option to use 'other' (which will allow you to type a username). In the username field, type your password; this will show the password and that way you can verify that it is typed correctly. Why I suggest this is that the keyboard layout might be wrong (e.g. UK instead of US).

---

### Post by kerry_s on 2011-08-20
I'm thinking bad install, perhaps try again.

---

### Post by akoskm on 2011-08-20
> **marshall1349 said:**
> I installed lubuntu over xubuntu and now whenever I enter the username and password it again asks for my username and password...

How these two actions happen exactly, does the login screen:
a) accept your password, the login screen disappearing for a moment then comes up again, or
b) it warns you about incorrect password, and asks for password again?

Assuming that this is a fresh install in case of a) your desktop installation maybe "corrupted". Downloading the ubuntu image again, [checking for md5sum ]("https://help.ubuntu.com/community/HowToMD5SUM") would be the easiest solution. b) your password is obviously wrong, but it doesn't mean that the installation itself isn't corrupted, so a) again.
Hope this helps.

---

### Post by marshall1349 on 2011-08-20
I have to type my username to login.....and the keyboard layout is correct I tried typing it in the username block....And when I type in my password and press enter immediately the username box comes up.like a never ending loop the screen doesn't go blank....And i installed lubuntu from a dvd...(did not have any blank cd's)

---

### Post by akoskm on 2011-08-20
> **marshall1349 said:**
> I have to type my username to login.....and the keyboard layout is correct I tried typing it in the username block....And when I type in my password and press enter immediately the username box comes up.like a never ending loop the screen doesn't go blank....And i installed lubuntu from a dvd...(did not have any blank cd's)

Is there any warning about incorrect login? Or it is just switching back without any warning to the username box?
Have you tried to log-in like Wim Sturkenboom suggested in [his post]("http://ubuntuforums.org/showpost.php?p=11168967&postcount=2")?
Eventually, this may help: [Login incorrect]("http://ubuntuforums.org/showthread.php?t=775330").

ps.: you can also [install ubuntu from an USB drive]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by marshall1349 on 2011-08-20
Tried everything you guys told me.....The login screen just switches back to the username box...no errors no warnings....should I try a fresh install of lubuntu???This time with a cd???And my pc is too old does not support usb boot...but does show my usb drive (if plugged in) in the bootable devices menu as a hard disk but does not boot up....What should I do???

---

### Post by whatthefunk on 2011-08-20
Id do a fresh install.  Do you have a CD drive?

---

### Post by amjjawad on 2011-08-28
Hi there,

I'll do my best to help even if I won't answer your question(s) directly.

1- [https://help.ubuntu.com/community/Lubuntu/GetLubuntu#11.04](https://help.ubuntu.com/community/Lubuntu/GetLubuntu#11.04)
Please get Lubuntu 11.04, [check MD5SUM and compare the hashes]("https://help.ubuntu.com/community/UbuntuHashes").

2- Create a LiveCD (CD-R -- I never tired another type) and please make sure to burn it at a low speed (8x).

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

3- If your Machine doesn't boot from USB then: [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

Just in case you want to give it a try :)

4- Insert your LiveCD, enter BIOS and make sure your CDROM is the first device to boot from.

5- Choose the Manual Installation.

6- IF and ONLY IF Lubuntu will be the ONLY OS installed on that machine, then please: Create New Partition Table.
The installer will give you that option.

7- Create minimum 2 partitions:

a- Root - Mount Point ( / ) and type ext4
b- Swap - Linux-Swap

/home partition (ext4) is recommended.


Now, check if you can login.



For shutdown issues:

Accessories > LXTerminal

Please run: 

```
sudo shutdown -P now

```

---


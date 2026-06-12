---
title: "Login"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by rneamand on 2010-04-10
I have just installed a power supply in a Sony PCV-RS420 that was given to me. Like other posts I have read I am having trouble figuring out how to change the username and password for Ubumtu. (Linux) I was able to change the password but I guess I screwed up when I entered root for the useradd. Can anyone help me out. I have read all the posts I could find but, I am confused and have no experience with Linux let alone Ubuntu. Thanks

---

### Post by lisati on 2010-04-10
For info on root access in Ubuntu have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Gixxy on 2010-04-10
sorry... was the machine given to you with ubuntu already installed?
i am just wondering what a psu change has to do with a uname/psswd. :confused:
are you asking how to reset a password with a live cd?

---

### Post by rneamand on 2010-04-10
Yes. The machine was doa. It was given to me by a friend of a friend. I installed a new power supply and now the machine works but, when it boots this Ubunta screen comes up and asks for a user name and password. I have no disks for it. The computer tag on the back says Windows XP is installed but someone must have reconfigured it with Linux and added Ubumta.

---

### Post by jrothwell97 on 2010-04-10
Assuming the machine is now yours and this is not a repair job, might I suggest downloading, burning and doing a fresh install of Ubuntu?

(You can use ShipIt if you have a slow connection.)

---

### Post by rneamand on 2010-04-10
downloaded newest version of ubumbu on my pc on thumb drive and cd iso. Neither one will install on Sony. Still goes directly to the ubumbu screen and wants username and password.

---

### Post by Rex Bouwense on 2010-04-10
Check your boot order and make sure that the cd drive will boot before the hard drive and that your Sony will boot from a USB flash drive.  Some computers do not have that capability.  After you downloaded the ISO did you check the md5sum to insure that you had a good download?  That could be another reason it is not loading.

---

### Post by uRock on 2010-04-10
To get your system to boot Ubuntu from the cd, you may need to hit the F12 key or F2 key to be able to select which device to boot from.

Cheers,
Ronnie

---

### Post by sisco311 on 2010-04-10
> **rneamand said:**
> downloaded newest version of ubumbu on my pc on thumb drive and cd iso. Neither one will install on Sony. Still goes directly to the ubumbu screen and wants username and password.

You have to set the CD-ROM or USB stick as the first boot device in BIOS.

Or boot into recovery mode & reset the password:
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---


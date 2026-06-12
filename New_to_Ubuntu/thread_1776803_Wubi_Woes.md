---
title: "Wubi Woes"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Formerly on 2011-06-06
My Windows OS was having a big virus attack that didn't seem like it would be able to be fixed. So I decided that I would switch it over to Linux, I already have one computer that is. But it would not read off the Linux CD I have of Jaunty Jackalope, so I had to install from the website ... Here's where the trouble begins.

Upon installing through Wubi it instantly partitioned my two operating systems, I wanted only Linux. Now when I start up my computer I have three options--Linux, Windows, or F8 to see options for starting Windows. No matter how far I look into google or what software I install under Linux I cannot find a way to remove Windows and make Linux my primary OS.

Furthermore I'm having two other issues, one is that I'm getting an odd amount of lag. The computer I previously mentioned and the one I'm currently using are the same yet this one runs very smoothly. The other issue is that I cannot seem to change the appearance as deeply as I'd like to.

Under the computer I'm currently running, I can install to the desktop, on the top I see "applications, places, system" and on the bottom I see what window I'm currently on ... Under the aforementioned computer everything is on the left under this chunky black bar, seems I can only run one of any application at a time even! So in short, I'm wondering how to fix any of these issues?

edit -- To be clear, I can't even seem to find the terminal under the aforementioned computer... Even how funny that sounds...

---

### Post by coffeecat on 2011-06-06
> **Formerly said:**
> Upon installing through Wubi it instantly partitioned my two operating systems, I wanted only Linux. Now when I start up my computer I have three options--Linux, Windows, or F8 to see options for starting Windows. No matter how far I look into google or what software I install under Linux I cannot find a way to remove Windows and make Linux my primary OS.

If you installed through Wubi, you cannot remove Windows without removing Ubuntu as well. Ubuntu is installed in a virtual hard drive within the Windows partition. Remove Windows and Ubuntu goes as well. If you want only Ubuntu, you will have to install it to its own partition from the install CD.

> **Formerly said:**
> Under the computer I'm currently running, I can install to the desktop, on the top I see "applications, places, system" and on the bottom I see what window I'm currently on ... Under the aforementioned computer everything is on the left under this chunky black bar, seems I can only run one of any application at a time even! So in short, I'm wondering how to fix any of these issues?

I'm a bit confused as to which computer is which, but no matter! The "aforementioned" computer sounds from your description as though  it is running the Unity desktop. The "current" one is running classic gnome. More about Unity:

[http://omgubuntu.co.uk/natty/](http://omgubuntu.co.uk/natty/)

---

### Post by migs73 on 2011-06-06
WUBI is not a true install and should only really be used for evaluation purposes.

WUBI writes a virtual File system inside a windows folder. If you remove windows you will remove your Ubuntu as well. It is possible though to transfer to a full install;

[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

I've never tried it so cannot comment on how good/easy it is.

The lag could be because it is a Wubi install also, although I have never found this in any Wubi install I've done (including this one I'm writing on!)

Good Luck

Mike

---

### Post by Brian0312 on 2011-06-06
I'd guess that your lag issues is probably be related to your Windows Virus.  Because WUBI is installed on a virtual drive under windows and is therefore inherently linked to windows, you're problem wasn't solved.  I'd personally see if you can download a new ISO and burn it to CD/DVD/USB and install the traditional way.  I'm sure it will be a much happier experience.

---

### Post by Formerly on 2011-06-09
I can't burn CDs and I don't have a USB drive that's big enough.

So I tried UNetbootin. The installer worked fine, it created a separate partition for itself named "Unetbootin" but when attempting a full install I noted some difficulties. The installation appears to be on the Ubuntu screen, as an icon. Everything runs fine, selecting the language, time, ect. When selecting the file I get a "No root file system is defined" message. This is for 10.04

When using google the answers appear to be both to use the suggested route and to use "/" if I read them correctly. This is odd because I did use the suggested route and I cannot see "/"

edit -- I should also add it's telling me "Your installation is on /dev/sda2/ you will not be able to ... " and I'm assuming that's part of the issue but I cannot tell how to fix that.

---

### Post by jtarin on 2011-06-09
> I can't burn CDs and I don't have a USB drive that's big enough.
[USB flash drive]("https://help.ubuntu.com/community/Installation/FromUSBStick")

    A Netbook installation requires a minimum 1 GB USB flash drive.
    Desktop or server requires a 2 GB USB flash drive.

---

### Post by Formerly on 2011-06-09
> **jtarin said:**
> [USB flash drive]("https://help.ubuntu.com/community/Installation/FromUSBStick")

    A Netbook installation requires a minimum **1 GB USB flash drive**.
    Desktop or server requires a 2 GB USB flash drive.

As stated in exactly what you quoted, I _do not_ have a flash drive big enough. The route I decided to go with is told to be one that is capable. All I want to do is install Linux without a CD or USB.

---

### Post by jtarin on 2011-06-09
I think it is telling you a partition is not defined for Ubuntu.There are several options. [Look here]("http://sourceforge.net/apps/trac/unetbootin/wiki/installmodes") for the different install methods to try and determine what is best for your situation. Still needing help? Post back

---


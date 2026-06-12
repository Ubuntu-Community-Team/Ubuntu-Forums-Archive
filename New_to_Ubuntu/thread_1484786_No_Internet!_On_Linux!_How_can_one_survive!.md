---
title: "No Internet! On Linux! How can one survive?!"
date: 2010-05-16
forum: New to Ubuntu
---

### Post by BunnyDee on 2010-05-16
I have a WiFi connection to the internet, not sure what model the router is as it's "inside" but it's some Pirelli do. My network card is... well, a Realtek 8185 Extensible 802.11b/g I believe it says here.

The thing is, I am able to connect to the Internet through win7, but, ever since I upgraded from Ubuntu 9.04 to 10.04 (only had the first one for a few hours), it's unable to connect, although it sees my network, but has absolutely no reception, for some reason.

Oh, and if your answer involves installing drivers, please would you tell me what to do with the downloaded files, there's no self-installing .exe here or anything.

Thanks a million to anyone who even *tries* to reply, and generally anyone who puts up with my cluelessness.

---

### Post by commondork on 2010-05-16
I believe that Realtek provides a Linux driver for your card here: [http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352")

If that is your card and that looks like the correct driver (please verify) for it then download it.  It should download to your Downloads directory.

From the terminal change your working directory to your Downloads directory which should be /home/yourusername/Downloads with the following command:

```
cd /home/yourusername/Downloads
```
Then run this command from the terminal:
```
tar -zxvf rtl8185_linux_26.1031.1207.2009.release.tar.gz
```
When that's done change into the rtl8185_linux_26.1031.1207.2009.release directory.  You can read the README file from the command line or by using the GUI.  

A quick overview of what you'll do next is type ```
make
``` from the command line within the rtl8185_linux_26.1031.1207.2009.release directory, then ```
make install
``` then you'll reboot and bring up your wifi card with the ```
ifconfig wlan0 up
``` command.  You might need to slap the word sudo in front of that last command.  Hope this or any of this helps you out!

---

### Post by commondork on 2010-05-16
It just occured to me that you can't download from within Ubuntu so wherever you place the tar.gz file is where you'll perform those commands (except the last).  Sorry for any confusion!

---

### Post by k3lt01 on 2010-05-16
> **BunnyDee said:**
> although it sees my network, but has absolutely no reception, for some reason.This says, to me at least, it is not a driver issue. I would recommend that you follow the steps in [this post]("http://ubuntuforums.org/showpost.php?p=3996845&postcount=5").

Let us know how you go.

---

### Post by 3rdalbum on 2010-05-16
Find out the chipset model by using the "lspci" and "lsusb" commands.

Then search for the chipset model plus "ubuntu 10.04". I have a feeling that there's an inappropriate driver attaching to your wireless card, that is causing it to not connect. If you blacklist that driver (whatever it is), then the correct driver can take over.

Doing that search that I recommended should tell you if this is the case.

Do this BEFORE installing that driver mentioned a few posts above mine.

---

### Post by BunnyDee on 2010-05-16
Thank you so much for your prompt replies, people! I'm amazed at how fast people reply here!

I haven't done all that yet, but I will do soon (as soon as I reboot and try things out in Ubuntu) and will update you all...

---


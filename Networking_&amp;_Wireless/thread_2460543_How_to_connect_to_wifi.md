---
title: "How to connect to wifi?"
date: 2021-04-13
forum: Networking &amp; Wireless
---

### Post by anaberga on 2021-04-13
Hello,
I'm a total non-tech person who somehow managed to follow the recipe and install Ubuntu 20.04 on my old macbook pro 2011. However i see no way to connect to wifi automatically. The instructions on the page [Ubuntu Desktop Guide]("https://help.ubuntu.com/stable/ubuntu-help/index.html.en")[COLOR=#AEA79F][FONT=Ubuntu] » [/FONT][/COLOR][Networking, web & email]("https://help.ubuntu.com/stable/ubuntu-help/net.html.en")[COLOR=#AEA79F][FONT=Ubuntu] » [/FONT][/COLOR][Wireless networking]("https://help.ubuntu.com/stable/ubuntu-help/net-wireless.html.en")[COLOR=#AEA79F][FONT=Ubuntu] »[/FONT][/COLOR]"Connect to a wireless network" don't work as there's nothing pertaining to Wifi on the 'system menu' on the top right.

I then went ahead and installed Ubuntu 20.10, thinking that maybe wifi would be easy to connect on that one but, same thing. I still have this version on my machine.

I did a search and whatever results i found involved terminals and commands which are foreign to me. Is there a relatively easy way for me to make wifi work on my computer, or would it just be easier to find someone and have them fix it for me?

Thank you,
Ana

---

### Post by ActionParsnip on 2021-04-13
Why 20.10? It only has 9 months support and so is EOL (End of life) in July. If you are non-technical then I suggest you wipe the install off and do a clean install of 20.04. This is LTS (Long term supported) for 5 years and is rock solid.

Does the system have a make and model, please?

---

### Post by anaberga on 2021-04-13
HI, thank you. I explained above that I switched to 20.10 in the hopes that it'd be easier to connect wifi. I'd have gladly kept 20.04 if I'd been able to make the wifi work (I still have 20.10 on my machine at the moment)
I'm not sure what you mean by system? I downloaded the Ubuntu versions on this page [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

If you're talking about the computer, it's  a Macbook pro 13 inch, early 2011. Is that what you're asking?

---

### Post by slickymaster on 2021-04-13
*Thread moved to **Networking & Wireless**.*

---

### Post by chili555 on 2021-04-13
> Is there a relatively easy way for me to make wifi work on my computer, or would it just be easier to find someone and have them fix it for me?Here I am! I'm ready, let's go!

If you can see nothing about wireless, then it typically means that there is no existing wireless driver.  Let's check and find out.

The 'relatively easy' way is to use the terminal. It gathers information quicky, easily and accurately. Please open a terminal Ctrl+Alt+t and type:

```
lspci -nnk | grep 0280 -A3
```That pipe symbol | is on the right side of my US keyboard on the same key with \. lspci means list all the PCI devices and grep 0280 means limit the result to wireless.

Press enter. The command will show needed details about your built-in wireless card. Post the result in your reply and we'll proceed.

Here is the result from my machine, for example:

```
chili@T440p:~$ lspci -nnk | grep 0280 -A3
03:00.0 Network controller [[COLOR="#FF0000"]0280[/COLOR]]: Intel Corporation Wireless 7260 [8086:08b2] (rev 83)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c270]
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi
```That's how we know if you have an Intel card, a Realtek card, an Atheros card, etc., and which exact device.

---

### Post by anaberga on 2021-04-13
HI, 
Thank you so much - i did that and here's what it says

Network controller [0280]: Broadcom Inc. and subsidiaries BCM4331 802.11 a/b/g/n [14e4:4331] (rev 02)
	Subsystem: Apple Inc. Airport Extreme [106b:00d6]
	Kernel driver in use: bcma-pci-bridge
	Kernel modules: bcma

What next?

---

### Post by chili555 on 2021-04-13
Please see: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

In short, get a temporary internet connection by ethernet, tethering or whatever means possible and, again, in the terminal:

```
sudo apt update
sudo apt install -y firmware-b43-installer
```Reboot and enjoy your wireless!

---

### Post by anaberga on 2021-04-13
Where can i find instructions on how to do this?
[COLOR=#000000]get a temporary internet connection by ethernet, tethering or whatever means possible [/COLOR]

---

### Post by chili555 on 2021-04-13
Does your computer have an ethernet port? Plug a cable into it and the other end into your router. It ought to connect automatically.

[https://www.makeuseof.com/tag/tethering-use-mobile-internet-pc/](https://www.makeuseof.com/tag/tethering-use-mobile-internet-pc/)

---

### Post by anaberga on 2021-04-13
Just saw the link. Thank you very much, you basically solved the whole thing for me.

What i still don't understand is why this isn't integrated into the installation. Very grateful to be able to test Ubuntu, but easily configurable wifi would be a giant step towards user friendliness outside of the tech community. I've a feeling there's going to be a spike in Ubuntu downloads very very soon.

Thank you again

---

### Post by anaberga on 2021-04-13
When I type the first line, [COLOR=#000000][FONT=&quot]sudo apt update [/FONT][/COLOR] it's asking me for a password...

---

### Post by anaberga on 2021-04-13
Is this supposed to be s[COLOR=#000000][FONT=&quot]udo apt update (ENTER), and then the second line?[/FONT][/COLOR]sudo apt install -y firmware-b43-installer

---

### Post by anaberga on 2021-04-13
OK, after some trial and error I typed [COLOR=#000000][FONT=&quot]sudo apt update | [/FONT][/COLOR][COLOR=#000000][FONT=&quot]sudo apt install -y firmware-b43-installer all in one line, then used the password i set up during the install. Finally worked &#128077;&#127995; Thank you [/FONT][/COLOR]

---

### Post by chili555 on 2021-04-13
> What i still don't understand is why this isn't integrated into the installation. Ubuntu is released as free and open source software. You can download the source code, read and understand every bit of it, modify it, republish it and basically about anything you want within the rather broad and permissive guidelines of the GNU General Public License (GPL). [https://en.wikipedia.org/wiki/GNU_General_Public_License](https://en.wikipedia.org/wiki/GNU_General_Public_License)

Once you introduce proprietary (read: secret) elements, the operating system is no longer strictly free and open source. The Broadcom firmware is indeed proprietary. Therefore, in order to ship Ubuntu as free and open source, Broadcom firmware files may not be included.

They may, as you have seen, be installed easily after installation. Most of us are not rigid about the firmware; we just want working wireless!

> Is this supposed to be sudo apt update (ENTER), and then the second line?sudo apt install -y firmware-b43-installerIndeed. When commands are on two lines in a forum post, it, by custom, means 'run the first command to its completion, noting any errors or warnings and then proceed to the next command until all commands are completed.'

If the commands were intended to be one long line, it would have been:

```
sudo apt update && sudo apt install -y firmware-b43-installer
```The && means to do the first command and, if it completes successfully, next do the second command.

I don't usually like the all-in-one method because I like to look for informative clues, errors, warnings, smoke or sparks (ha ha!) before I proceed to the next step.

You first experience with the terminal wasn't bad at all. Your wireless works!

---

### Post by anaberga on 2021-04-14
Thank you Chili &#55357;&#56397;&#55356;&#57339;

---

### Post by smith11ardis on 2021-04-14
Click to Wifi icon and then enter password.

---


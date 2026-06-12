---
title: "Help for a total newbie please."
date: 2019-01-12
forum: Networking &amp; Wireless
---

### Post by mrfdes on 2019-01-12
Hello everyone,
I am new to this forum, just as I am totally new and almost completely ignorant to Linux.
The only things I do know about Linux so far are things I have read or heard, but I hope experience and help I will be finding (including here) wil help to change that.

Now for my problem:
I installed lubuntu 18.10 x86 today on an old, low-spec Asus laptop.
I was very impressed with how flawlessly it installed, how good it runs and especially how much HDD space it left me with.

My only problem so far is, I have no idea how to connect to my home network (WiFi).
I could immediately connect to the Internet, just had to enter my password and I was connected.
However, the laptop is not seen on any of the other machines (all running Windows 10), and the NAS is not recognised.

Could someone please help me in as plain English as possible how to connect to the network so the laptop shows up?

I have had advice such as "Click on the folder you want to share [COLOR=#333333][FONT=&amp]and choose the “Local Network Share” option, but I do not have that option.
After that the trouble begins, as they start talking about nautilus-share and things like that, and that is where they lose me completely.

So, could anyone help me further in very plain language, please?

Any help will be very much appreciated. ;)

[/FONT][/COLOR]

---

### Post by chili555 on 2019-01-12
> I have had advice such as "Click on the folder you want to share and choose the “Local Network Share” option, but I do not have that option.Not even if you *right-click *the folder you wish to share?

Is nautilus-share installed?```
sudo apt update
sudo apt install nautilus-share
```

---

### Post by mrfdes on 2019-01-12
Sorry, that is what I meant, but I typed it wrong here.
The advice was indeed to [COLOR=#ff0000]**right-click**[/COLOR] on the folder.

Nautilus-share is not installed, not as far as I can see. I looked in Internet (probably a stupid place to look), System Tools, Preferences, LXQt Settings, but I found nothing that even remotely looks like it.

Do I enter that sudo code into the QTerminal?
From what I can see, I assume that installs nautilus-share. 
Once it is installed, what do I do then?

Sorry if my questions are stupid, but as I said, I am a Linuxignoramus. :D

Thank you for your contribution.

---

### Post by chili555 on 2019-01-12
> Do I enter that sudo code into the QTerminal?Correct. One line at a time, followed by Enter.> 
Once it is installed, what do I do then?The safest step is to reboot and then try the right-click again.> 
Sorry if my questions are stupid, but as I said, I am a Linuxignoramus.
No worries; all of us were newbies at one time; even me and even Linus Torvalds!

---

### Post by mrfdes on 2019-01-12
> **chili555 said:**
> The safest step is to reboot and then try the right-click again.
I'm afraid the desired option does not appear when right clicking.
No [COLOR=#333333]“Local Network Share” option to be found, yet it looks like nautilus-share installed correctly, no error messages or nothing, and I did reboot after installation.

[/COLOR]Nevertheless, I am very grateful for your help.

---

### Post by chili555 on 2019-01-12
Please try:```
sudo apt install samba
```Reboot and report, please.

Also, open your file browser and find the menu item, 'About' and tell us what it reports.

---

### Post by mrfdes on 2019-01-12
No, still no change.
Still the same result as before with nautilus.
:mad:

---

### Post by chili555 on 2019-01-12
> Also, open your file browser and find the menu item, 'About' and tell us what it reports.
We need to know if you are running 'Files' (formerly known as nautilus) in Gnome or Thunar or Dolphin or what else.

We suspect one of the latter since you:> installed **lubuntu **18.10 x86 today on an old, low-spec Asus laptop.As you may suspect, methods to achieve file sharing vary between Gnome, which is feature-rich and therefore heavy and lubuntu/xubuntu which are hot-rods and lightweight.

Mrs. Chili thinks that Ubuntu's ability to be customized to almost any hardware is its greatest weakness and, simultaneously, its greatest strength.

---

### Post by mrfdes on 2019-01-12
Righty-Ho,
See attachment for full details.
[IMG]https://www.vlaanderen-flanders.org.uk/Pics/aboutlubuntu.jpg[/IMG]

---

### Post by chili555 on 2019-01-12
I think, I hope I have found it! In the terminal, do:```
sudo apt install system-config-samba
sudo touch /etc/libuser.conf
sudo system-config-samba
```Use the green **+**, for Add to browse to a folder to share. Check off Visible and also Allow access to everyone.

This works here from Ubuntu to Ubuntu. I have no experience with Windows.

---

### Post by mrfdes on 2019-01-12
Chili555,
YOU ARE A STAR!!!!!!!
I really don't know how to thank you.

I followed the steps you explained, looked on my Windows laptop, went to Network, refreshed, and there it was.

Thank you ever so much.
Your help was INVALUABLE, yours and Mrs. Chili555's.

Thanks again.

---

### Post by chili555 on 2019-01-12
Awesome! Glad it's working.

Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

### Post by mrfdes on 2019-01-12
I certainly will.

Just one more thing: do I have to comnplete any more steps to make the Linux laptop see the Windows machines, as it is not recognising them at the moment, although I haven't got a clue how that happens on Linux.
I have noticed though, that the icon, previously called "Network" is now called "Windows Network".

Anyway, a million thanks again.

---

### Post by chili555 on 2019-01-12
I believe that when you open the pcmanfm-qt file manager, you will need to browse network and then specify the location of the Windows files. I think you connect to server and specify something like: ```
smb://192.168.x.y
```...where 192.168.x.y is the IP address of the Windows computer.

---

### Post by mrfdes on 2019-01-13
OK,
thank you.
I'll give that a try later.

I owe you big time.

---


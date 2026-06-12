---
title: "Netspeed for Xubuntu."
date: 2020-12-20
forum: Networking &amp; Wireless
---

### Post by gardenair on 2020-12-20
hi,
     I m using **Xubuntu **on my laptop. I need to install software which may tell me internet speed.I just google and find **NetSpeed **software for Ubuntu. How may I use such kind of  software for my Xubuntu desktop?

Thanks.

---

### Post by T6&amp;sfpER35% on 2020-12-20
[https://askubuntu.com/questions/1232539/how-to-install-netspeed-in-ubuntu-20-04](https://askubuntu.com/questions/1232539/how-to-install-netspeed-in-ubuntu-20-04)

might help

---

### Post by Holger_Gehrke on 2020-12-20
There's a plugin for the XFCE panel named network monitor (package xfce4-netload-plugin). It will show you current total upload and download speed either numerical or graphical (or both). 

Holger

---

### Post by gardenair on 2020-12-20
Thanks  Holger_Gehrke for the reply. Well I shall be regretful if you kindly let me know the complete command/methos  for " xfce4-netload-plugin " installation.

---

### Post by CelticWarrior on 2020-12-21
> **gardenair said:**
> Thanks  Holger_Gehrke for the reply. Well I shall be regretful if you kindly let me know the complete command/methos  for " xfce4-netload-plugin " installation.

It's software like any other, available in the Ubuntu repositories. It can and should be installed like any other software:
```
sudo apt install xfce4-netload-plugin
```
or use any GUI tool for the same purpose.

---

### Post by gardenair on 2020-12-21
Thanks for the reply. Well I use the terminal windows and it shows the output as. Unable to locate** netload **software. KIndly view the snap.

---

### Post by Holger_Gehrke on 2020-12-21
It's already installed, but since it's a plugin for the panel you don't call it like a normal program. Instead you right click on the panel you want to add it to and choose 'Panel'->'Panel Settings' (attention: I'm translating from German to English since my system uses German; the actual name of options or menu choices might differ). Go to the 'Objects'-tab in the form which will be displayed. Click the green plus-button on the right side of the form. A new form opens with all the plugins you could add. Select 'Network Monitor', click on the button 'Add' (at the bottom of the form) and the button 'Close'. You should now be back in the 'Panel Settings' form and the network monitor should be at the bottom of the list (and should also be visible at the right end of the panel). You can use the up and down button at the right side of the panel to move the plugin in the list (and in the panel). Hit the button with the cog-icon to open the settings for the network monitor. Most of the settings are purely cosmetic except for the name of the network interface to monitor. I usually use 'ip link' in a terminal to get a list of the interfaces. For a wired connection it should be something like 'enp1s0' and something like 'wlp1s0' for wlan.

Holger

---

### Post by gardenair on 2020-12-22
Thanks  " Holger_Gehrke "  for guiding me. AS to your kind instructions i am still unable to load " **netload**" software in my panel .Though Xubuntu  says that the software is already installed .An attachment is enclosed here with as screen short.

---

### Post by Holger_Gehrke on 2020-12-22
It's not on the list of available plugins as 'netload', so searching for that will fail. It's called "Netzwerkmonitor" in my German XFCE, which should translate to "Network Monitor". Unless I completely misread your screenshot, you've already added it to the panel but have a wrong name for the network interface, because you've got the text 'Net' followed by two empty vertical bar graphs at the very right on your panel. That's what the Network Monitor looks like by default.

Holger

---

### Post by T6&amp;sfpER35% on 2020-12-22
what Holger_Gehrke said is correct 
right click on **toolbar - panel - add new items** then click **network monitor** and click **add** at the bottom and **close**
you'll then see it on the panel showing net and two bars
to change that right click on it and **properties**.By **network device** you have to type in your network device
(can also change the bars to show values under **properties)**
to find your network device: 
```
inxi -Fxzd
```
and under** network** look for IF: xxxx , that's your network device


(there's probably a better command to find your network device,but i don't know it lol)

---

### Post by gardenair on 2020-12-23
Thanks for the replies.Appreciate it. Well as to your instructions i successfully add "** Network Monitor" ** on my panel. Now the issue is I browse on internet but i can't see any statistic on it ? The Net Monitor is on grey  colour.
May be there is a need to add " **Network  device** " name. Kindly guide me what name may I add in it so it may work.

---

### Post by The Cog on 2020-12-23
The command ```
ip route list default
``` will tell you the device name for talking to the internet. For example, here's mine:
```
default via 192.168.0.1 dev [COLOR=#0000cd]**eth0**[/COLOR] proto dhcp metric 100
```

---

### Post by T6&amp;sfpER35% on 2020-12-23
seems you have two devices you connect through? try either one and see what it does,i'm not sure.
either add **eno**l or **wlp3s0** to network device name

edit: like [COLOR=#ff6633]**The Cog**[/COLOR] said is better lol
> [COLOR=#000000](there's probably a better command to find your network device,but i don't know it lol)[/COLOR]
and there it is

---

### Post by gardenair on 2020-12-23
Thanks all for your kind assistance/guidance.The " ** "[B] Network Monitor" ** [/B]is working. 
There are many commands in linux,The thing that I want to ask about the following  commands while are related to  laptop hardware.```
 inxi -Fxzd 
``` also ```
dmsg 
``` what are the difference in between these.In my opinion which I understand is " **dmesg** " is more in detail  output about the hardware while " **inxi -Fxzd **"  shows very precise .

```
ip route list default
```
**ip route**  is also a new command for me. Where I may learn about such commands which may helpful for analysing or configuring new things.

---

### Post by Holger_Gehrke on 2020-12-23
You can learn about commands through the manual and it's search function. The command to view the manual of a command is 'man command' (for example 'man dmesg') and the search is called with 'apropos keyword'. 'apropos' uses an index of all the words in the first paragraphs (which always contains a synopsis of what the command does) of all manual pages. Of course there's a manual page for 'apropos'. 

'inxi' is actually a shell script that uses a lot of other commands to gather and format information about the hardware and software of the system.

'dmesg' on the other hand does something else entirely. It displays the messages that the kernel generates and can also be used to control the buffer in which these messages are stored. If something goes wrong in your system the kernel will leave a message about it in that buffer and 'dmesg' allowes you to view those messages.

Holger

---

### Post by The Cog on 2020-12-23
> **gardenair said:**
> 
**ip route**  is also a new command for me. Where I may learn about such commands which may helpful for analysing or configuring new things.
ip is a huge command. I use **ip route** and **ip address** a lot. But you will likely never need to know most of its options. I certainly don't.
Don't try to learn all possible commands. Just keep using the system, asking for help when you need it (as you have been doing), and reading about aspects that interest you. You will find about lots of commands, and slowly accumulate a set that you find useful and use a lot. You will also find many other commands that you just note that such things are possible, so you know roughly what to look for if you ever have need.

Everyone collects their own set of tools. They pick them up as they go along.

That said, there are lots of introductory web sites like these. Again, you don't need to memorise them all, but knowing they exist is a good start.
[https://ubuntu.com/tutorials/command-line-for-beginners#1-overview](https://ubuntu.com/tutorials/command-line-for-beginners#1-overview)
[https://linuxnewbieguide.org/overview-of-chapters/more-advanced-guides/i-dont-know-any-commands/](https://linuxnewbieguide.org/overview-of-chapters/more-advanced-guides/i-dont-know-any-commands/)

---


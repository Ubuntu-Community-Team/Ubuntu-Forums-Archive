---
title: "Yet another network/ wireless problem......"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by kpaddler on 2010-01-03
[SIZE=4]Hi, I'm hoping someone can help me. I finnally took the plunge and installed Ubuntu on a lap-top that had windows Vista. This was a complete install, I got rid of the Vista all together. My problem is that the laptop has a switch with an indicator light that lets the user turn on/off the wireless for the internet, networking, etc. The light shows it is off, no matter which way the switch is, and I cannot access the internet. I've tried the system check-box, which did not help. If I was still using windows I'm pretty sure I could go into device manager and figure it out from there, but with Ubuntu, I'm lost. Please help.[/SIZE]

---

### Post by cariboo on 2010-01-03
First we need to know what wireless device you have. Because you don't have a network connection, you'll have to use the terminal to do some troubleshooting. Go to Applications-->Accessories-->Terminal, and type:

```
sudo lshw -C network > network.txt
```

Type in your password when asked, it will not be echoed back. The above command will create a text file called network.txt with all the details of your network devices, that you can copy to your Windows partition. Please paste the text file in your next post.

BTW, please use the default text formatting in your posts, they won't get answered any faster using a large font.

---

### Post by kpaddler on 2010-01-04
I copied the command line down exactly, (I'm pretty sure, I tried it a few ways to make any way) and I only get "sudo: lshw: command not found" although it did ask me for my password at one point. 
 
BTW I use a larger font because I am vision impaired, not because I am "shouting" or thinking I will get an answer sooner, if it makes you happy, I will squint.
 
Thanks

---

### Post by USB_NL on 2010-01-04
here you get some info:
```
iwconfig
```

---

### Post by USB_NL on 2010-01-04
more info for iwconfig
```
iwconfig --help
```for all connections use 
```
ifconfig
```and for help
```
ifconfig --help
```

---

### Post by bkratz on 2010-01-04
> **kpaddler said:**
> I copied the command line down exactly, (I'm pretty sure, I tried it a few ways to make any way) and I only get "sudo: lshw: command not found" although it did ask me for my password at one point. 
 
BTW I use a larger font because I am vision impaired, not because I am "shouting" or thinking I will get an answer sooner, if it makes you happy, I will squint.
 
Thanks

Did you maybe type in a 1 or an I; just copy/paste his command in it actually was a lowercase "L"

---

### Post by kpaddler on 2010-01-09
iwconfig,   comesback with a "no wireless extentions" message
 
ifconfig at least comes back with a message about packets sent / recieved being zero, but does not mention what kind of wireless equipment I have. 
 
I thought I might have typed in the original command line wrong, (switching 1 for l etc) so I tried it both ways. I can't copy/ paste from a web page with the Ubuntu machine becase the wireless does not work which is why I'm here. I'm posting on a Windows PC and trying the sugesstions on the Linux machine. 
 
Does anyone know anything else I can try?

---

### Post by Paddy Landau on 2010-01-09
> **kpaddler said:**
> I use a larger font because I am vision impaired...
If you use Firefox as your browser, you can tell Firefox to make everything bigger, so you can read our posts, too. Either use menu option View > Zoom, or try Ctrl++ (bigger), Ctrl+- (smaller) and Ctrl+0 (reset).

> **kpaddler said:**
> I finnally took the plunge and installed Ubuntu on a lap-top that had windows Vista. This was a complete install, I got rid of the Vista all together.
For future reference, always use the Live CD to test *before* you make the decision to get rid of Windows. If the Live CD can access the Internet, play videos and record sound, and display correctly, then you have a good chance. Then install on a separate partition (i.e. dual-boot), so that you still have access to your Windows in case it all goes wrong. I had a year of dual-booting before I finally got rid of Windows. Some people never get rid of it.

> **kpaddler said:**
> I only get "sudo: lshw: command not found"...
What version of Ubuntu have you installed? It doesn't sound right that you don't have it. Go to System > Administration > Synaptic Package Manager. On the right side, scroll down to lshw. It should have a green block next to it. If not, click the grey block, select Mark for Installation, and press Apply. Then try again.

---

### Post by USB_NL on 2010-01-11
[SIZE=4][B]Proably if you give your laptop type info people can help much better 
and even better might be soundcard info i guess[/B][/SIZE]

sucses

---


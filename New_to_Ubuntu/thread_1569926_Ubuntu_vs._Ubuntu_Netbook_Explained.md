---
title: "Ubuntu vs. Ubuntu Netbook Explained"
date: 2010-09-07
forum: New to Ubuntu
---

### Post by silverglade00 on 2010-09-07
There have been a lot of posts asking about the netbook version. Hopefully this will help clear up some of the confusion...

**Can Netbook edition run on my laptop/desktop/etc?**

There is nothing special about the netbook edition that is specific to netbooks. You can run it just fine on a netbook, regular laptop, desktop computer, even a server computer if you want. It does not have any special wireless abilities or other optimizations that are specific to netbooks only, with one exception. 

**What's different about the netbook version?**

That exception is the main interface. The netbook edition has a customized Gnome interface that is better suited toward the funky resolutions that smaller netbooks have. That said, it will work just fine on other computers. I have used it on a 15" laptop and on a desktop. It features a customized menu that takes over the desktop area of the screen. It also has settings that maximize almost every window that opens to full screen so that you can read it.

**Do I have to install the Netbook edition to get the custom menu? If I do not like it, how do I get regular Ubuntu?**

If you already have Ubuntu installed and want to try the netbook interface, type the following into Terminal:
```
sudo apt-get install ubuntu-netbook
```
Log out, choose a Ubuntu Netbook Edition session on the sign-in screen and log in.

If you already have Ubuntu Netbook Edition installed and want to use the regular interface, type the following into Terminal:
```
sudo apt-get install ubuntu-desktop
```
Log out, choose a Gnome session on the sign-in screen and log in.

Feel free to add any other tips/tricks/thoughts about Ubuntu vs. Netbook Edition to this thread. Also, let the mods know if you think this should be a sticky.

---

### Post by Willynux on 2010-11-14
I've just downloaded the netbook edition (curiosity) and installed it because I was not aware of this. But i'm using a 15" screen and both editions look just exactly the same to me. I also tried what you said in terminal but still nothing changed. I wonder if the system just is aware of your hardware and installs the desktop version instead...

---

### Post by Jechem on 2010-11-14
I have installed 10.04 UNE and uninstalled the netbook launcher coz i chose to use the gnome desktop but ubuntu-desktop package is not installed according to synaptic. I know it doesn't make sense but it works fine.:confused:

---

### Post by uRock on 2010-11-14
> **Willynux said:**
> I've just downloaded the netbook edition (curiosity) and installed it because I was not aware of this. But i'm using a 15" screen and both editions look just exactly the same to me. I also tried what you said in terminal but still nothing changed. I wonder if the system just is aware of your hardware and installs the desktop version instead...

Hello and welcome to the forums.

No matter what hardware you have it should look the same. I am playing with UNE on my netbook and I think Unity looks great. I can't wait for 11.04 to come out as it is supposed to be even faster than the current version.

---

### Post by fatharraxman on 2010-11-15
I have 10 in screen netbook I installed ubuntu netbook interferance 14 days ago, that was the first time to see linux in my 31 year old live, I aked myself then where have I been? three days latter I uninstalled netbook and installed ubuntu desktop interference it works nice and fast but when open Evolution mail at creating account steps chunk, the buttons of forward is not appearing and you can not continue the process only pressing enter and the menu
would not resized smaller it may resize bigger but not smaller 
this answered my question in a thread why threre is two interferences  while the netbooks are capable to use the the two efficiently 
What I am sorry for; is for what stupid action to of me (as a new ubuntu user) to erase one interference for another while they both could be beautifully customized with themes and backgrounds and buttons from Gnom-art web site through : system>Preferences> Appearance>  get more thems online, on the left of the menu, download them and come back to preference menu click over install and enjoy 
You can only simply adapt the one you got first, I hope I did know that 14 days ago,hahahahahaha,what a stupid novice, but more to tell, may be there is a secret bigger than what my new ubuntu brain think upon making two different interferences, maybe your small device will have a longer live span with netbook ! I don't know but I swear this is not only for fun.
I would like to ask you what if the commands you gave will install a real full interference or just a theme inside oanothere one ?
:popcorn:

---

### Post by nlsthzn on 2010-11-15
@OP, thanks for the info... I suspect I will be installing the normal interface for my netbook just because Unity in its current form is too slow... (saves me doing a re-install which I was contemplating)...

---

### Post by fatharraxman on 2010-11-15
I agree Ubuntu desktop is faster than Ubuntu netbook in my 1gb ram 1.6 atom *hp* mini and faster than windows starter and the noise I hear not knowing where they come from appear in netbook but not in Ubuntu and you feel as if you have wider horizon with wider freedom field than in netbook but still there must be a serious reason for creating a netbook interference in linux world

---

### Post by fatharraxman on 2010-11-22
I discovered how easy today to switch between Ubuntu, Ubuntu-netbook, and KDE, all what you need is to look to the bottom after choosing user on logging in, thank you SeijiSensei [IMG]http://ubuntuforums.org/customavatars/avatar698195_1.gif[/IMG]
he who told me that

---

### Post by eric948470 on 2011-06-07
I first installed the 11.04 desktop edition. Then I entered
```
sudo apt-get install ubuntu-netbook
```in the terminal. Synaptic marks the package "ubuntu-netbook" as installed. When I logged out and logged back in, I didn't get a choice to switch to the netbook edition.

How do I switch to the netbook edition?

Edit: I also tried restarting. Didn't work.

---

### Post by snowpine on 2011-06-07
> **eric948470 said:**
> I first installed the 11.04 desktop edition. Then I entered
```
sudo apt-get install ubuntu-netbook
```in the terminal. Synaptic marks the package "ubuntu-netbook" as installed. When I logged out and logged back in, I didn't get a choice to switch to the netbook edition.

How do I switch to the netbook edition?

Edit: I also tried restarting. Didn't work.

You're bumping an outdated thread.

Ubuntu Netbook no longer exists; it has been combined with Ubuntu. ubuntu-netbook is synonymous with ubuntu-desktop as you can see here:

[http://packages.ubuntu.com/natty/ubuntu-netbook](http://packages.ubuntu.com/natty/ubuntu-netbook)

---

### Post by eric948470 on 2011-06-07
Thanks.

I thought I searched, but looks like I could have done better. Apologies.

---


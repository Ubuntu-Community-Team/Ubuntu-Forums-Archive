---
title: "Am I missing something here?"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by jmhenbest on 2010-06-22
I am a long time Windows user who decided to install a dual boot XP/UBUNTU system on an old (1999) Dell Pentium III. The dual boot works fine as does XP. I cannot get UBUNTU to recognize my NIC (NE2000 ISA etc.). In researching the problem and possible solutions I consistently get instructions to use terminal commands. All fine and good if you happen to know UNIX. I thought the necessity of using the command line disappeared in maybe 1995(?) in the Windows world. Does UNBUNTU really require terminal commands to make many inquiries or configuration changes? Is there some reasonably modern graphical interface to use or do I really need to learn to use arcane terminal commands?

---

### Post by Bachstelze on 2010-06-22
> **jmhenbest said:**
> I thought the necessity of using the command line disappeared in maybe 1995(?) in the Windows world.

Yes, because in the Windows world, hardware manufacturers are nice enough to release drivers with nice point-and-click installers. Blame your NIC's manufacturer for the fact that you have to use the command-line, not Linux.

---

### Post by james_xxx on 2010-06-22
No offense is intended by this whatsoever, but if you simply have no interest in using the command line at all, Linux is probably not the Operating System for you.

It is worth mentioning that learning even just basic BASH commands, and learning to write even the most basic command line scripts can really go a long way in making your experience with Linux much nicer. The scariness wears off quickly.

In most any Operating System, Windows very much included, many tasks can just simply be done much more efficiently and quickly via the command line.

Additionally, I know of no OS in which there is a GUI tool available for every command line tool.

---

### Post by amauk on 2010-06-22
it's not that it's *required*
but it sure makes life easier (for both helper and helpee)

GUI instructions will differ depending on the desktop environment being used
Helper will have to write half-a-dozen versions of the same instructions to cater for Gnome, KDE, XFCE, LXDE, etc. etc.

As the helpee, you have to carry out these instructions manually
Click this, Select that
There's no way to ease the process

CLI on the other hand is (by and large) system agnostic
the same instructions apply to every system

And as the helpee, you can just copy & paste CLI commands into the terminal
No clicking, and hardly any typing

---

### Post by jerome1232 on 2010-06-22
Windows works very hard to shine the interface up for the user. Linux doesn't always do this.

The command line isn't an old arcane way of doing things as you think. For certain tasks it's simply the best way. It's also easy to automate tasks using command line programs. As mentioned above when searching for answers, even if there's a gui way of doing it, it's simply easier to give the command line instructions for several reasons.

Most linux gui's are simply frontends that are still using the command line tools in the background (clicking a button is simply generating a command with the correct options)

There are often *several* different gui's for the same task, all with buttons in different spots. The gui's also tend to change where they put their buttons more often version to version than command line programs tend to change their options and their meanings version to version.

It's harder to describe "Click the green thing in the lower half portion of your screen, next to the white box with an orange circle" than it is to say copy and paste this

```
a bunch of gloobly glock commandline instructions
that seems to go on for ten paragraphs, thankfully we can
select all and copy and paste it. Let it do it's magic
```

---

### Post by philinux on 2010-06-22
> **jmhenbest said:**
> I am a long time Windows user who decided to install a dual boot XP/UBUNTU system on an old (1999) Dell Pentium III. The dual boot works fine as does XP. I cannot get UBUNTU to recognize my NIC (NE2000 ISA etc.). In researching the problem and possible solutions I consistently get instructions to use terminal commands. All fine and good if you happen to know UNIX. I thought the necessity of using the command line disappeared in maybe 1995(?) in the Windows world. Does UNBUNTU really require terminal commands to make many inquiries or configuration changes? Is there some reasonably modern graphical interface to use or do I really need to learn to use arcane terminal commands?

According to this it is possible to get that card to work. It does require some cli stuff though but very minor.
[http://www.linuxforums.org/forum/linux-networking/16827-ne2000-isa-drivers.html](http://www.linuxforums.org/forum/linux-networking/16827-ne2000-isa-drivers.html)

First try this. Open a terminal, apps>accessories and use this command. Just type your login password at the prompt at hit enter, it does not show the password. 

```
sudo modprobe ne
```

There's also this.
[http://ubuntuforums.org/showthread.php?t=281319](http://ubuntuforums.org/showthread.php?t=281319)
Someone else may chime in to help with this.

---

### Post by jmhenbest on 2010-06-22
[FONT=Arial][SIZE=3]Thank you all for your replies. I have learned much STUFF in my past. I will need to learn more STUFF in my future if I wish to take advantage of UBUNTU. This is, in my opinion, why Linux will never be the OS of choice in most large commercial installations. Too much non-intuitive STUFF for too many people.[/SIZE][/FONT]

---

### Post by philinux on 2010-06-22
> **jmhenbest said:**
> [FONT=Arial][SIZE=3]Thank you all for your replies. I have learned much STUFF in my past. I will need to learn more STUFF in my future if I wish to take advantage of UBUNTU. This is, in my opinion, why Linux will never be the OS of choice in most large commercial installations. Too much non-intuitive STUFF for too many people.[/SIZE][/FONT]

Imagine you had never used windows. The learning curve would be very steep too.  Also that nic card looks like a problem for some in windows. Is it relatively old?

[http://www.windowsnetworking.com/articles_tutorials/wxpne2k.html](http://www.windowsnetworking.com/articles_tutorials/wxpne2k.html)
[http://www.google.com/search?hl=en&q=NIC+NE2000+ISA&btnG=Search&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?hl=en&q=NIC+NE2000+ISA&btnG=Search&aq=f&aqi=&aql=&oq=&gs_rfai=)

---

### Post by Arla on 2010-06-22
> **jmhenbest said:**
> Thank you all for your replies. I have learned much STUFF in my past. I will need to learn more STUFF in my future if I wish to take advantage of UBUNTU. This is, in my opinion, why Linux will never be the OS of choice in most large commercial installations. Too much non-intuitive STUFF for too many people.

Setting up network cards is NOT something that most people in a large commercial installation will do.

That's a job for the network/computer maintainers, and if they don't have the knowledge, perhaps others should be hired who do.

I hardly ever touch the terminal on my personal machine anymore because I did all the setup, and now don't need to go there, I also used to still regularly use the cmd prompt under windows because the GUI's were lacking in the ability to do certain things (or lacking the ability to do them half as easily).

---

### Post by ken631 on 2010-06-22
> **jmhenbest said:**
> [FONT=Arial][SIZE=3]Thank you all for your replies. I have learned much STUFF in my past. I will need to learn more STUFF in my future if I wish to take advantage of UBUNTU. This is, in my opinion, why Linux will never be the OS of choice in most large commercial installations. Too much non-intuitive STUFF for too many people.[/SIZE][/FONT]
 
Actually linux/unix is in most corporations running in the background on a server. The windows machines connect to it through ethernet cables.  
 
I remember first getting into linux my first choice was Mandrake which broke and I ran away from it after I couldn't get it back up again.
 
I knew a few people, they may be a dying breed or extinct by now, who were so puritist they refused to use a GUI and ran everything on the command line.

---

### Post by Mark_in_Hollywood on 2010-06-22
Just a Thought:

With the high quality of help available in this forum, you will probably only have to open a terminal and cut & paste commands into it. And, you DO NOT HAVE TO KNOW Unix what-so-ever.

That is not very different from using Windows CMD "terminal". (screenshot attached)

---


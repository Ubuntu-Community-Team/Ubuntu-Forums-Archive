---
title: "Super Newb"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by windowsbrainwashed on 2009-10-25
Hello Linux users,
 
I was hoping to try out Ubuntu or Kubuntu. However, I already have the ISO burned to a disc and pretty much set up the Live CD. I ran that while in Windows to use the install in windows option to preview Kubuntu with dual boot up. I also have used Wubi to install Ubuntu but removed it. 
Now, a little question seems to pop up in my mind. I am not trying to change this operating system for all those that love CLI, but as you can tell from my username I am so used to Windows I actually like it. I really like the GUI interface Windows Explorer and the simplicity of using Windows. I am aware that Kubuntu employs a GUI as well, but its not very helpful to poor me.
That said, as I mentioned I tried Kubuntu, and I had no idea how to install Adobe Flash player for Konquerer (or maybe i should just remove that altogether and install Firefox?). I have no idea why the activate button is giving me some kind of error when trying to install the latest Nvidia driver after clicking activate. Honestly, yes it is free, but for the love of God is this really supposed to be so complicated? 
I really don't want to have to learn code and for some reason Adept or Synaptic is not anywhere to be found where prior forums have said that they are located so I can get to installing some basics. Adept is not in my systems folder or directory anywhere from what i am seeing. I really am not sure if there are guides to Kubuntu for the Super Newb or not? And why doesn't all this stuff(ie Adobe Flash, Java, or perhaps just the Universal or multiverse repo? whatever that is) have an auto prompt to install it all for me after scanning my systems hardware?
I need a REALLY good IDIOTS guide here. ((RED ALERT)) please help.

---

### Post by bwang on 2009-10-25
If you are using Firefox, Flash can be installed from Adobe's website. You'll want to get the .deb package.
Also, at some point in Linux you'll have to use the command line. It's one of Linux's most powerful tools. You don't really need to learn "code"--copy and paste usually works fine.
As for the auto-prompt thing, not everyone wants or needs Flash or Java.
What error do you get when trying to install the Nvidia driver? What are your hardware specs?

---

### Post by Dennis N on 2009-10-25
Get this free guide and read it. It will answer many questions.

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by windowsbrainwashed on 2009-10-25
> **bwang said:**
> If you are using Firefox, Flash can be installed from Adobe's website. You'll want to get the .deb package.
Also, at some point in Linux you'll have to use the command line. It's one of Linux's most powerful tools. You don't really need to learn "code"--copy and paste usually works fine.
As for the auto-prompt thing, not everyone wants or needs Flash or Java.
What error do you get when trying to install the Nvidia driver? What are your hardware specs?
 
I've got an Intl i7 920 on an ASUS p6t se board with 4gb ddr3 dual channel RAM, Nvidia 8500gt, and and old WD caviar HDD with some LG dvd player that at least works.  Kind of in the process of still upgrading, HDD only uses SATA I, errr.

---

### Post by Warren North on 2009-10-25
You will actually be surprised how many things you can do in GUI.
If you have a quick question I google it first (type question in google) and it usually takes me to this forum where the answer is at. If is has to be a terminal command you can usually for the command copy and paste it in terminal using shift ctrl V or paste.

---

### Post by windowsbrainwashed on 2009-10-25
> **Dennis N said:**
> Get this free guide and read it. It will answer many questions.
 
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
 
 
yeah already scanned that one, wasn't much help with any of my issues on the first pass through it at least.  Kewl book tho.  Why can't Ubuntu or Kubuntu come with a window that pops up and says Hi there Mr Newb, Linux is a CLI system mostly and here are some commands you'll need to know right away...lol.  But thanks anywho guys might leave this open for a little whiel to see if anyone else knows of a great site for absolute beginners, or free books other then this one.

---

### Post by hashimoto on 2009-10-25
> **windowsbrainwashed said:**
> ...if anyone else knows of a great site for absolute beginners...

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by jmszr on 2009-10-25
wbw,

First, in the Terminal, copy & paste:

```
sudo apt-get install kubuntu-restricted-extras
```

and press Enter. It will ask for your password - type it in  (it won't be visible - security) and press Enter. That should help with Java, Flash, and codecs among others.

I don't want you to get the wrong idea, but you might want to check out: [http://www.kubuntuforums.net/](http://www.kubuntuforums.net/)

Hope that helps.

Edit: If Java wants you to agree to their EULA press Tab to OK it and then Enter.

Edit: Edited to reflect Post#11

---

### Post by Abu_Dayya on 2009-10-25
You have to know that:

- Linux is not mostly CLI. I rarely open a terminal. Whatever you do with a terminal and some commands, you can do with the GUI.

- Java and Flash are also not installed by default in Windows.

- Saying 'learining linux is harder than learning windows' or 'windows is very easy and user friendly' is not necessarily true, its really relative. I mean you call yourself 'windowsbrainwashed', so I'm sure you are quite good with windows now. And I know you are computer savy judging by the choices of your computer hardware, but I bet you didn't know that much five years ago (or whenever you STARTED using windows). So, if it took you a few years to learn windows, and it will take you a few months to learn ubuntu (BTW installing flash is very easy), I say linux is more user friendly and is much easier than windows or mac.


Believe me, you will love it. Just needs a little patience

---

### Post by Dennis N on 2009-10-25
Abu_Dayya has it exactly right. I would add that as time goes on, I think a new user who is willing to educate himself a bit about Linux commands will begin to find many uses for the CLI that make tasks easier (such as simple scripts, alias commands, etc.)

[Back before the 1990's when you started your new DOS PC all you began with was C:\> (inviting you to type some DOS command).]

---

### Post by The Cog on 2009-10-25
> **jmszr said:**
> wbw,

First, in the Terminal, copy & paste:

```
sudo apt-get kubuntu-restricted-extras
```

and press Enter. It will ask for your password - type it in  (it won't be visible - security) and press Enter. That should help with Java, Flash, and codecs among others.


I think that should probably be:
```
sudo apt-get install kubuntu-restricted-extras
```

---

### Post by Ms_Angel_D on 2009-10-25
> **windowsbrainwashed said:**
> Hello Linux users,
 
I was hoping to try out Ubuntu or Kubuntu. However, I already have the ISO burned to a disc and pretty much set up the Live CD. I ran that while in Windows to use the install in windows option to preview Kubuntu with dual boot up. I also have used Wubi to install Ubuntu but removed it. 
Now, a little question seems to pop up in my mind. I am not trying to change this operating system for all those that love CLI, but as you can tell from my username I am so used to Windows I actually like it. I really like the GUI interface Windows Explorer and the simplicity of using Windows. I am aware that Kubuntu employs a GUI as well, but its not very helpful to poor me.
That said, as I mentioned I tried Kubuntu, and I had no idea how to install Adobe Flash player for Konquerer (or maybe i should just remove that altogether and install Firefox?). I have no idea why the activate button is giving me some kind of error when trying to install the latest Nvidia driver after clicking activate. Honestly, yes it is free, but for the love of God is this really supposed to be so complicated? 
I really don't want to have to learn code and for some reason Adept or Synaptic is not anywhere to be found where prior forums have said that they are located so I can get to installing some basics. Adept is not in my systems folder or directory anywhere from what i am seeing. I really am not sure if there are guides to Kubuntu for the Super Newb or not? And why doesn't all this stuff(ie Adobe Flash, Java, or perhaps just the Universal or multiverse repo? whatever that is) have an auto prompt to install it all for me after scanning my systems hardware?
I need a REALLY good IDIOTS guide here. ((RED ALERT)) please help.

Hi there, and welcome to ubuntu/kubuntu. If your wishing to try Kubuntu Here is a great tutorial It really helped me when getting started with kubuntu

[The Perfect Desktop - Kubuntu 9.04]("http://www.howtoforge.com/the-perfect-desktop-kubuntu-9.04")

That tutorial has screenshots and everything and should be about what your looking for ;). I hope this info helps.

Angel

---

### Post by Ant. on 2009-10-25
Everyone has to start somewhere and everyone is a complete noob at the beginning. When I first started everything I done via the terminal was literally a copy & paste job from somewhere else, but eventually you learn how to do things slowly. Also if you a competent Windows user you should be experienced in using command prompt to do various tasks. Once you get used to Ubuntu and realise how fast, secure and efficient it is in comparison to Windows you will never look back :P When you learn some of the commands you will use the terminal quite a bit as it can be very useful and efficient for certain things. Thats not to say you have to use it, the average user who does day to day stuff like browsing, e-mail, IM, office stuff, etc could get away with never using CLI.

Like already mentioned most stuff can be done via the GUI. Also you may want to try a different window manager, you can [_install GNOME_]("http://www.psychocats.net/ubuntu/gnome") or Xfce. You never know you may prefer it to KDE.

> I have no idea why the activate button is giving me some kind of error when trying to install the latest Nvidia driver after clicking activate. Honestly, yes it is free, but for the love of God is this really supposed to be so complicated?Regarding this, usually the best thing to do when it comes to hardware is put the hardware's name & model into google along with the word linux or ubuntu after it. Usually one of the first few results will be extremely useful, or there might even be a thread on these forums about the graphics card in question. Have you tried [_searching?_]("http://ubuntuforums.org/search.php")

This is a pretty useful guide for getting common software and alternatives to Windows software installed on your Ubuntu machine:
[http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/](http://theindexer.wordpress.com/2009/04/24/to-do-list-after-installing-ubuntu-904-aka-jaunty-jackalope/)

Have fun with Ubuntu and give it a chance ;)

---


---
title: "Adding Repositories to Ubuntu 10.10"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by ROVDude on 2011-06-03
:confused:
 
OK, I feel like a total idiot. I took two terms of "Linux/Unix Administration" like 12 years ago in college. Pretty cool. So I thought I'd give Ubuntu a try on my Asus Netbook1005HA. Turns out a buddy had a copy of 10.10, so that worked out. Installed it from a thumbdrive, and I was really happy with that. Then came the installation of applications. D'OH! (I'm really a noob when it comes to this, so please, act like you're replying to a four year old!). I want to add repositories so when I search for apps I can find them. So, HOW DO I ADD REPOSITORIES using Synaptic or editing Software Sources, or do I have to use Terminal and manually edit the file? ARRRRGGGGHHH!!!!!!
 
OK....took my meds.....I'm good.
 
Anyway, if someone can walk me through step by step how to add a repository (i.e. EasyUbuntu), I'd really appreciate it.
 
Thanks!

---

### Post by GrouchyGaijin on 2011-06-03
> **ROVDude said:**
> :confused:
 

Anyway, if someone can walk me through step by step how to add a repository (i.e. EasyUbuntu), I'd really appreciate it.
 
Thanks!

Did you look at this? [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by ROVDude on 2011-06-03
Actually, yes, I did.  I searched around quite a bit.  For example, the article has a section on "Adding PPAs".  Is that what I'm supposed to do?  And if so, it's something more than just putting in a URL for the system to search.  I tried that, didn't work.  So what do I type in where?  Any guidance?

Thanks.

---

### Post by GrouchyGaijin on 2011-06-03
> **ROVDude said:**
> Actually, yes, I did.  I searched around quite a bit.  For example, the article has a section on "Adding PPAs".  Is that what I'm supposed to do?  And if so, it's something more than just putting in a URL for the system to search.  I tried that, didn't work.  So what do I type in where?  Any guidance?

Thanks.

A PPA is a third party repository.  That means Ubuntu (Canonical) doesn't check or service any of the software in that repository.

Take the conky companions PPA for example:

> You can update your system with unsupported packages from this untrusted PPA by adding ppa:conky-companions/ppa to your system's Software Sources.

From the page you read about installing PPAs:

> 
Adding PPAs
Since Ubuntu 9.10, there is an easy way to add Personal Package Archives to the software sources that automatically imports the keys to verify the downloaded software.

As described above, go to System > Administration > Software Sources > Other Software and click Add. You can then type in an APT line in PPA form, like ppa:[username]/[ppaname].


So for conky companions you would paste ppa:conky-companions/ppa

into the blank field shown in the screenshot below:

[IMG]http://dl.dropbox.com/u/23115609/Add-PPA.png[/IMG]

You can get to this window by going to Synaptic > Settings > Repositories > Other software > Add

---

### Post by corncob on 2011-06-03
> **ROVDude said:**
> Actually, yes, I did.  I searched around quite a bit.  For example, the article has a section on "Adding PPAs".  Is that what I'm supposed to do?  And if so, it's something more than just putting in a URL for the system to search.  I tried that, didn't work.  So what do I type in where?  Any guidance?

Thanks.

  A good one to add is the Medibuntu repository.  Follow the instructions at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and you'll have your media up and running.

---

### Post by jtarin on 2011-06-03
Open a terminal and issue the command ```
gksudo gedit /etc/apt/sources.list
```Copy and Post the results. This is your sources list file that "apt" uses when looking for available software. I usually use Synaptic for all my package needs, but also some command line.I find both dependable. I edit my sources.list from time to time

---

### Post by wojox on 2011-06-03
> **corncob said:**
> A good one to add is the Medibuntu repository.  Follow the instructions at [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu) and you'll have your media up and running.

+1, I don't even think EasyUbuntu is supported anymore.

---

### Post by ROVDude on 2011-06-03
*+1, I don't even think EasyUbuntu is supported anymore. 	*

So what do I do if I find a repository that I do like?  I mean, what Corncob sent for a command is probably a bit beyond what I would be able to come up with!  (see prior post)  I'm not really thinking about anything I need in particular.  Just thinking about what may happen in the future.  I mean, I don't want to be relying on everyone else's help forever, right?

Thanks.

---

### Post by jtarin on 2011-06-03
> **ROVDude said:**
> *+1, I don't even think EasyUbuntu is supported anymore. 	*

So what do I do if I find a repository that I do like?  I mean, what Corncob sent for a command is probably a bit beyond what I would be able to come up with!  (see prior post)  I'm not really thinking about anything I need in particular.  Just thinking about what may happen in the future.  I mean, I don't want to be relying on everyone else's help forever, right?

Thanks.Corncob's command can be copied and pasted, if you want to use it, as can most apt -get commands you find around in your travels. There are also third-party applications that are usually added one at a time from a ppa....don't worry about ppa's each ppa page gives you instructions on how to add to your list. These are unsupported _officially_. Package management is one of Ubuntu's most desired features and also one of the most confusing to newbies. Ask questions and Google to learn.

---

### Post by el_koraco on 2011-06-03
> **ROVDude said:**
> *+1, I don't even think EasyUbuntu is supported anymore. 	*

So what do I do if I find a repository that I do like?  I mean, what Corncob sent for a command is probably a bit beyond what I would be able to come up with!  (see prior post)  I'm not really thinking about anything I need in particular.  Just thinking about what may happen in the future.  I mean, I don't want to be relying on everyone else's help forever, right?

Thanks.

One way is to do what was described above. You can also go to the Software Center, Edit, then Software sources. Then you go to the software tab, click Add, and paste the PPA or repository URL. PPA+s are probably what you mean when you say adding other repositories. 

In the command line, you can type 

```
sudo add-apt-repository ppa:whatever

```


The only repository commonly being added that is not a PPA is the Medibuntu repository. A difference is that PPA's automatically add GPG keys, which are a means of verification that code to the repository has been added only by developers with permits. When you are adding repositories that are not PPA's to your sources list, you need to import the GPG key, and instructions are usually provided.

---

### Post by ROVDude on 2011-06-04
Folks, I sincerely thank you all for your posts and assistance.  I think I sort of have an understanding of what's going on, and look forward to using Ubuntu as my main OS.
 
You know, I got to thinking; While using Windows, if I got a data file or whatever and I couldn't open it with any apps I had, what did I do?  I Googled it, went online, searched around, and found what I needed to open and use the data.
 
So, really, what's the big difference between doing that, and what I'm doing with Ubuntu?  With that mindset, hey, things are just as well, plus the added security and sense of accomplishment of understanding something extremely foreign to me.
 
Again, thanks for all the help, and I look forward to working through more bugs, problems, and re-installs!  :D  Very pleased!
 
 
Now let's see......how do I close this thread out as solved....hmmmmm.........

---

### Post by jtarin on 2011-06-04
You discovered in Windows,the same path that's used in Linux.

---


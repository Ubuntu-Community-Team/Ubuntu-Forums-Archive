---
title: "Virtual CD/DVD Read/Write player???"
date: 2010-08-29
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-08-29
Hello:

If my Lenovo X61 laptop is not plugged into its base, I have no DVD player.

Does a virtual DVD R/W player exist?

If so, would VirtualBox recognize it so that I could download linux ISO images and then install them using VirtualBox?

Is this question ridiculous?

Thanks,

Rob.

---

### Post by Vaphell on 2010-08-29
virtualbox part - yes, you can install systems having their .iso files. In VB properties you add isos to the list, pick one to act as a physical drive and give VB a spin.

---

### Post by 1991sudarshan on 2010-08-29
> **Robert.Thompson said:**
> Hello:

If my Lenovo X61 laptop is not plugged into its base, I have no DVD player.

Does a virtual DVD R/W player exist?

If so, would VirtualBox recognize it so that I could download linux ISO images and then install them using VirtualBox?

Is this question ridiculous?

Thanks,

Rob.

the fact to say that your question is not ridiculous :P!!
you can mount the iso in ubuntu!! you just have to right click on the iso and select the mount option from  the menu!!!

---

### Post by trigsenior on 2010-08-29
**Right click mount**

Read your post a few time still not quite sure what you want. This is what I think you're asking for , To mount .iso files on linux. If so this can be easily archived. You can install a program called **gmountiso** 
TO install , either search in synaptic or simply in terminal run.

```

sudo apt-get install gmountiso

```

Good luck!

---

### Post by varunendra on 2010-08-29
Or, if you need a virtual drive emulator like daemontools in windows, then you should try **cdemu**. As far as I have experienced, it is the only program that actually **emulates** a cd/dvd drive. All other tools are just different methods of accessing the contents of iso & other cd/dvd images but they don't really emulate a physical drive. A very good thing about cdemu is that the list of supported formats is really lo...ng! Bad thing is - it sometimes gets a bit tricky to install & get it working :(. But hopefully, [this]("http://ubuntuforums.org/showpost.php?p=9181110&postcount=7") may help if you wish to try.

Or, more easily, just add these lines to your **Software Sources>Other Software** list (click on "Add" on that tab):
```
deb http://ppa.launchpad.net/cdemu/ppa/ubuntu lucid main
```and
```
deb-src http://ppa.launchpad.net/cdemu/ppa/ubuntu lucid main
```After adding these to the sources list, close the box. It will ask to reload, do it.

Then open Synaptic, type **cdemu** in the search box. Click on "Reload" again if nothing shows up (it happens sometimes :)).
Now in the now-showed up list, tick on **gcdemu** only. The rest of the dependencies will be automatically selected. Click on apply > let it install everything. Now follow only **steps** **11** & **12** of the post I've linked above. Restart and hopefully, you'll get a yellow-blue gcdemu applet on your top panel after restart.

It may all look too much of a hassle to follow, but believe me, it's worth it all!

[SIZE=2]**_End Note_:**[/SIZE]
[COLOR=Black]Just because of a long description, I don't mean that I'm recommending this to you. **[COLOR=DarkRed]You may be more than happy just by installing gmountiso[/COLOR]**. But if you ever felt need for an actual emulator for cd/dvd drives, then you may find this quite useful.[/COLOR]

---

### Post by Robert.Thompson on 2010-08-30
Once it is installed, which it is - thank you!, where do I find instructions on how to actually use it?

Thanks,

Rob.

---

### Post by varunendra on 2010-08-30
Um...., well,.. could you please make it clear whom your question is addressed to? And what did you get installed?

**PS:**
And.., if you got what you needed, how about marking the thread as [Solved]?

---

### Post by Robert.Thompson on 2010-08-31
> **varunendra said:**
> Um...., well,.. could you please make it clear whom your question is addressed to? And what did you get installed?

**PS:**
And.., if you got what you needed, how about marking the thread as [Solved]?

Sorry...

I installed cdemu.

Rob.

---

### Post by varunendra on 2010-08-31
It is okay.

I've mentioned the link where I found those instructions - at the top of the post whose link I've given here.

I'll tell you more about the interesting story-
I needed a virtual drive to be able to mount **non-iso** images such that VirtualBox could see & accept them as physical discs. I knew about cdemu at the time but found no easy way to install & configure it, so ignored it first. Then I tried almost a dozen other tools only to find out that VBox didn't recognize them at all.

Finally, as a last resort, I decided to take the plunge. Found that guide (similar to many others- actually, there seems to be no easier way out for it yet), struggled quite a bit since it didn't work as the guide suggested (you may be lucky one to get it straight), but as they say- "when you are truly desperate for something, you ultimately get it".

Getting it worked out successfully was a great feeling of achievement for me (I know it'll look childish & may even give me a good laugh later, but....). Once installed, it made things so convenient that proved it to be worthy of all the struggle.

However, I do wish to see it in the official repositories as an easily installable package, with no need for those post-installation steps.

Enjoy!:popcorn:

---

### Post by bodhi.zazen on 2010-08-31
> **Robert.Thompson said:**
> Hello:

If my Lenovo X61 laptop is not plugged into its base, I have no DVD player.

Does a virtual DVD R/W player exist?

If so, would VirtualBox recognize it so that I could download linux ISO images and then install them using VirtualBox?

Is this question ridiculous?

Thanks,

Rob.

Virtualbox will mount the iso as if it were a virtual cd drive. You can boot a linux iso without burning it to a CD and the virtualbox additions are provided on an iso.

[http://www.youtube.com/watch?v=Oobxm02UrBE](http://www.youtube.com/watch?v=Oobxm02UrBE)

The other solutions are for mounting the iso in Linux.

---

### Post by Robert.Thompson on 2010-08-31
Varun, you are going to hate this...

I have cdemu installed and running.

Now, wait for it...


  What do I do with it? and how do I do it?

Rob.

---

### Post by varunendra on 2010-08-31
> **Robert.Thompson said:**
> Varun, you are going to hate this...

I have cdemu installed and running.

Now, wait for it...

What do I do with it? and how do I do it?

Rob.

No.. absolutely not!!

If you've added its applet to the top panel as suggested in the linked post and it is active (looking blue-yellow), just click on it. It'll show two drives in a drop-down list. Clicking on any of them would open a browser window where you can browse to your cd/dvd image file & just double-click it. It'll get loaded in the virtual drive and be detected by the system as a physically loaded disc.

Follow [this]("http://www.my-guides.net/en/content/view/138/"). Follow the third (cdemu) method on that page.

Now where in these steps are you facing problem please post back. I'd be more than happy to help **anyone** with my favorite app.

---


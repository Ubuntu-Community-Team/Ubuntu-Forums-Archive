---
title: "Sorry, this is REALLY basic..."
date: 2009-01-26
forum: New to Ubuntu
---

### Post by SPARTAN1 on 2009-01-26
Trying to get a comms programme working for a friend, and I know ZERO about linux, being a Windows user...

I downloaded a programme called Intrepid (AX25) and placed it on the Desktop as I had no idea where else to stick it.  Double-clicking on it appeared to make it run, and it then said it had installed ok.  However, I cannot find any trace of it in any of the Application menus.

Where do I find it?  How do I start it running?

---

### Post by jespdj on 2009-01-26
Can you post a link to the site where you downloaded that program? Without knowing what program it is, it is very hard to help you with this.

---

### Post by SPARTAN1 on 2009-01-26
Went here:-

     [http://ubuntu.virginmedia.com/archive/pool/universe/a/ax25-apps/](http://ubuntu.virginmedia.com/archive/pool/universe/a/ax25-apps/)

Got this:-

     ax25-apps_0.0.6-16_i386.deb

---

### Post by -kg- on 2009-01-26
> **SPARTAN1 said:**
> Trying to get a comms programme working for a friend, and I know ZERO about linux, being a Windows user...

I downloaded a programme called Intrepid (AX25) and placed it on the Desktop as I had no idea where else to stick it.  Double-clicking on it appeared to make it run, and it then said it had installed ok.  However, I cannot find any trace of it in any of the Application menus.

Where do I find it?  How do I start it running?

Are you talking about installing the ax.25-apps for Amateur Radio Packet Radio communication, and installing it in Ubuntu 8.10 Intrepid (Ibex)?  Likely, you could have installed this from the repositories (which would have gbeen completely simple, but you didn't know).

A tutorial on this software is here:

[http://www.febo.com/packet/linux-ax25/index.html]("http://www.febo.com/packet/linux-ax25/index.html")

If this is what you installed, and since you claim no Linux experience, you are going to need further information and help with this, which, even though I am a Ham operator, I haven't got, since I haven't been into packet radio since the early to mid '90s, and not through linux, for sure.

If this is the case, we have another forum called Networking and Wireless which, though the networking concerned is actually conventional networking between computers on a LAN, you might possibly get better answers to your question...again, if my assumptions of installation of ax.25 networking is the case.

Also, you need a better, more descriptive title for your posts.  "This is really basic" doesn't explain the type of problem you're having, and is less likely to get the specific help you're needing.  It's just lucky that I'm a ham radio operator and was perusing the forums.

<edit>  OK, just saw your second post and it's just as I thought.  Yes, you could have installed this from the repositories under Synaptic (System/Administration/Synaptics Package Manager), but done is done, I suppose.  If it doesn't work right, I would suggest uninstalling and reinstalling through Synaptics.

I'm pretty sure there may be dependencies, and possibly a GUI to use with the apps, though as far as dependencies go, if you got a successful install, then there are no dependencies that your friends computer doesn't already have.  I'm thinking that it may be a command-line only program that is intended for use with a terminal type program. though without it installed and having experience with it, I have no way of knowing.

Anyway, the above still applies.

---

### Post by SPARTAN1 on 2009-01-26
Tried uninstalling and then reinstalling using the Synaptics Manager, but still the same.  Cannot find in the menu where it has put the startup options for this programme.

I think he hoped this would be relatively straightforward, but looking at the link you kindly provided has put us both off!

Thanks for your help which is appreciated...

---

### Post by bwang on 2009-01-26
Looking at the .deb, I see there are commands called listen and call.
Try running those from the terminal.

---

### Post by SPARTAN1 on 2009-01-27
Running either of those commands results in this message:-

axconfig: port 1 not active

Looked through to see if I can find where this needs activating, but no joy.

---

### Post by hyper_ch on 2009-01-27
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---


---
title: "X-server and Freevo"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by Phil Binner on 2009-03-11
I have a working Ubunto box with Intrepid Ibex, but I am new to this. I want to set up Freevo and have been directed to QuickStartGuide - Freevo 1.x Wiki. This says the first pre-requisite is a working X-Server. What is an X-Server. When I searched on the Freevo wiki it got no hits. A search on Google brought lots of hits, mostly for windows products that seemed to be trying to look like Linux, so does my Ubuntu box already have X-server, and if so how do I turn it on.

The quick start guide to Freevo installation seems to be giving me windows type instructions, i.e. download the package and install it. In my innocence I already set up Freevo using the synaptic package manager, and this seemed to go well. The installed package does not run, however. In fact it does nothing. Is this because i did not have an X-server before installation, or possibly just because i don't have one now. Do I have to ignore the synaptic package manager and do things the long way.

All help will be greatly appreciated

---

### Post by thtrgremlin on 2009-03-11
X server handles your video card to over simplify. If you can get to a desktop (instead of only having a command line) then X server is running.

How are you trying to run it, and what does it say when it fails? Are you running it from a terminal?

---

### Post by Weidbrewer on 2009-03-11
I guess that this isn't help, exactly, but I had the same issues with Freevo.  I never did get it working right.  That's why I ended up plowing through with MythTV.   I've been using that happily for a year and a half-ish.   It might be a little trickier to set up in some regards, but the community support is a lot better.   (There's even a Mythbuntu distro to build off of.)

---

### Post by Phil Binner on 2009-03-13
Now I've set up Freevo through the Synaptic Package Manager I get it through the Applications menu, and absolutely nothing happens, i'e' no messages. I did once find another way to attempt to run it, and I got a message saying I didn't have rights to the X-server. Unfortunately I cant remember how I got that, and I haven't been able to make it happen again. 

What facilities do you get from MythTV. Is it a complete sound and visual media centre. Ultimately I want to be able to access 2 or 3 sat cards and 2 digital terrestrial cards. I have no great commitment to Freevo.

My problem in accessing the documentation is the language it's written in. Whatever I read to do with Linux I find words I have no idea about. Not coming from a technical background brings it's own problems, but there are other conceptual problems. It actually took me a while to realise what 'distro' means. I am getting over this slowly but most documentation is difficult.

---

### Post by Phil Binner on 2009-03-13
Following reading teh previous replys I tried running from a terminal. I got teh following message:

"You are not part of the group 'freevo', you cannot exploit shared resources (such as the cache). Your data will be saved in /home/bigbin/.freevo 
Can't find all Python dependencies:
No module named utils

Not all requirements of Freevo are installed on your system.
Please check the INSTALL file for more information."

This seems fairly clear that the Symaptic Package Manager setup was not satisfactory. I'll go back and try installing the long way. I would welcome any comments about manual install rather than Synaptic Package Manager install.

---

### Post by Weidbrewer on 2009-03-14
As for what capabilities Myth has, I currently have a server running with 1.5TB of mirrored storage containing movies, music and pictures, as well as TV recorded through my tuner.   I have remote frontends (also running Myth) hooked up to the TVs of my house that can watch everything on the server.


I know exactly what you mean about the vocab needed for running Linux - there's a learning curve to any new process.   Like I said, the difference with Myth is that I found much better community support here and at [http://www.mythtvtalk.com/forum/](http://www.mythtvtalk.com/forum/).  If you have specific questions, I'll take a swing for you.

---

### Post by Phil Binner on 2009-03-15
Thanks. My specific query is about how many inputs MythTV can handle. I'm sure I'll sort the vocabulary eventually. Thanks for your help.

---

### Post by Weidbrewer on 2009-03-15
As far as I know, you're only limited by the number of tuners you have.

---


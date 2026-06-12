---
title: "FedoraPlus equivalent on Ubuntu."
date: 2011-04-02
forum: New to Ubuntu
---

### Post by salmontres on 2011-04-02
Hi everyone,

Fedora has a program called Fedora Plus, which sets up a good deal of programs when one installs the OS. Does Ubuntu have an equivalent program? If not, is there an auto script that will set up all of the basics for 64 bit (Flash, JRE, OpenBox, etc.).

---

### Post by fabricator4 on 2011-04-02
> **salmontres said:**
> Hi everyone,

Fedora has a program called Fedora Plus, which sets up a good deal of programs when one installs the OS. Does Ubuntu have an equivalent program? If not, is there an auto script that will set up all of the basics for 64 bit (Flash, JRE, OpenBox, etc.).

I think the problem with that is that everyone has a different idea as to what the ideal basic install is.  It should however be possible to write (or find) a script that does a lot of the basic installation for you.

A quick google search found [this page]("http://kuparinen.org/martti/comp/ubuntu/en/install.html") under section 4 which looks like it could be pasted into a script for running immediately after installation.

A trick that I like to use, since I maintain three machine for my own use, is to copy the .deb files in /var/cache/apt/archives from one machine to another.  You still have to run the updates and installs but since the relevant .deb files are already there the system doesn't have to download them again - it will just use them.  This saves me _heaps_ of bandwidth.  My philosophy is "download once, install many" :-)

Chris.

---

### Post by coffeecat on 2011-04-02
@salmotres, I suggest you be wary of scripts you find on the internet. They may not necessarily be malicious, but they may be badly coded.

A few years ago there was a 3rd-party app called Automatix, which was basically a complex script. It filled a true need but was heavily criticised by a senior Ubuntu developer. As described here:

[https://wiki.ubuntu.com/AutomatixIssues](https://wiki.ubuntu.com/AutomatixIssues)

That's all ancient history now, but you may find a utility called Ultamatix which has been based on Automatix. Perhaps the issues have been addressed; I don't know. But I wouldn't let Ultamatix anywhere near my system. Neither would I use any 3rd party script that I didn't understand myself.

You don't really need them. Install the package ubuntu-restricted-extras for flash, IcedTea (open source Java), ms core fonts and most of the video and audio codecs you'll need. Then enable the [Medibuntu]("http://www.medibuntu.org/") repository for libdvdcss2 and some other things. Finally, if you have specific needs, search in Ubuntu Community Documentation:

[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)

(There's a mass of stuff there.) Or the Ubuntu wiki:

[https://wiki.ubuntu.com/Home](https://wiki.ubuntu.com/Home)

You're unlikely not to find what you want. Indeed I recommend you use those two latter rather than some enthusiast's blog.

---

### Post by Rubi1200 on 2011-04-02
I totally agree with coffeecat about this.

Do not go down the path of scripts from the web or even copying and pasting something. You never know if something malicious has been coded into it.

For example, on the link you were given, one of the "recommended" applications is Firestarter. It is a firewall GUI but is deprecated and has not been maintained in a long time.

The links coffeecat provided should see you through.

The other thing to do is open and search through the Ubuntu Software Center; I am sure you will also find decent software in there.

---

### Post by salmontres on 2011-04-02
Thank you very much guys! I'll go ahead and mark the thread as solved.

---


---
title: "How to get Skype?"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by L Campbell on 2010-02-07
I went to the Skype website to download the program.

The Ubuntu option is Ubuntu 8.10+ 32-bit.

I have 8.04.4 and my question is, will this work for me?

Or what are my other options?

TIA.

---

### Post by HermanAB on 2010-02-07
Howdy,

You have a 50% chance: it will either work, or it will not...

When all else fails, download the 'Static' version from the Skype web site.  That one has all dependencies statically linked in, so it is a larger download, but it should work.  I always use that one, since it is less of a hassle than messing around with the other dysfunctional versions first.

---

### Post by Seithe on 2010-02-07
Yup it should work if you have a 32 bit than just download skype from there website, it'll open it up in deb and it should install with no problems, plus you can find skype in synaptic package manager.
system>administration>synaptic package manager. Search for skype a much more easier way. Or even another way just open your terminal Applications>Accessories>Terminal. Once opened type "sudo apt-get install skype" that should work!

---

### Post by marin123 on 2010-02-07
[http://adria.fesb.hr/~mbareta/skype](http://adria.fesb.hr/~mbareta/skype)

if you cant get skype to work try installing files from this link, they are files from medibuntu and i helped me to get my camera to work....

---

### Post by L Campbell on 2010-02-07
> **Seithe said:**
> Yup it should work if you have a 32 bit than just download skype from there website, it'll open it up in deb and it should install with no problems, plus you can find skype in synaptic package manager.
system>administration>synaptic package manager. Search for skype a much more easier way. Or even another way just open your terminal Applications>Accessories>Terminal. Once opened type "sudo apt-get install skype" that should work!

Hi, thanks for your interest however, Skype is no longer in Synaptic.

I'm sure I was using it about 2 weeks ago but it's not there now.

Kind regards.

---

### Post by s.fox on 2010-02-07
Hello,

If you are running a 32 bit system that one will be fine.

To check open a terminal and run this command:

```
uname -m
```

If it shows i686 then that link will be fine

If it shows x86_64 then you have a 64bit system.  Try following [this]("http://ubuntuforums.org/showthread.php?t=432295") guide to install correctly :)

-Silver Fox

---

### Post by mikewhatever on 2010-02-07
Synaptic is just a package manager and Skype was never there. There used to be packages in Medibuntu, was removed quite some time ago. In case the the .deb from skype.com doesn't work for you, I have all versions of Skype since 1.3 and will upload the one you need. Let me know.

---

### Post by switch10 on 2010-02-07
I can confirm that skype works on both, 64, and 32 bit installs of Ubuntu 9.10.  You can find the .deb [Here]("http://www.skype.com/download/skype/linux/choose/")

---

### Post by L Campbell on 2010-02-07
> **mikewhatever said:**
> Synaptic is just a package manager and Skype was never there. There used to be packages in Medibuntu, was removed quite some time ago. In case the the .deb from skype.com doesn't work for you, I have all versions of Skype since 1.3 and will upload the one you need. Let me know.

Thanks for your interest.

I now have the package, Intrepid_2.1.0.81_1_i386.deb  on my desktop.

I right clicked and chose "Open with GDebi package installer"

It began it's process, then stopped and gave me the error message,

'Error: Dependancy is not satisfiable:  libasound2

I went to Synaptic and found libasound2.  It was already installed but I re- installed it, but am still getting the same error message.

Kind regards.

---

### Post by mikewhatever on 2010-02-07
I think libasound and other dependencies (Qt, d-bus) changed too much since Hardy was released. Have you tried downloading the static package? It's basically an archive with the folder 'skype-static' in it. Unpack it and click on the 'skype' executable inside the folder.

---

### Post by L Campbell on 2010-02-08
> **mikewhatever said:**
> I think libasound and other dependencies (Qt, d-bus) changed too much since Hardy was released. Have you tried downloading the static package? It's basically an archive with the folder 'skype-static' in it. Unpack it and click on the 'skype' executable inside the folder.

Thanks again.

What I have found is:- 

[http://divyad.wordpress.com/2008/05/01/install-skype-on-ubuntu-804-hardy-heron-configure-sound/](http://divyad.wordpress.com/2008/05/01/install-skype-on-ubuntu-804-hardy-heron-configure-sound/)

[http://tiny.cc/rarh3](http://tiny.cc/rarh3)

It'll probably take me a while to stumble through this, so I will write back later.

Kind regards.

---

### Post by Georgia boy on 2010-02-08
What is the Skype-mid(Skype for Mids) I saw in the Snyaptic Package manager? I was reading here where Skype isn't in the package any longer and thought I had seen something about Skype there. When I went to the package manager this morning and did a search I found that listed and got to wondering what it was.


Tom

---

### Post by L Campbell on 2010-02-08
> **Georgia boy said:**
> What is the Skype-mid(Skype for Mids) I saw in the Snyaptic Package manager? I was reading here where Skype isn't in the package any longer and thought I had seen something about Skype there. When I went to the package manager this morning and did a search I found that listed and got to wondering what it was.


Tom

Hi, Tom, I am not able to find Skype in my Synaptic, either by doing a search or scrolling through manually.

I did find this from Google:-

[http://share.skype.com/sites/garage/skype_for_mids/](http://share.skype.com/sites/garage/skype_for_mids/)

Hopefully this will be of help to you.

Kind regards.

---

### Post by L Campbell on 2010-02-08
> **L Campbell said:**
> Thanks again.

What I have found is:- 

[http://divyad.wordpress.com/2008/05/01/install-skype-on-ubuntu-804-hardy-heron-configure-sound/](http://divyad.wordpress.com/2008/05/01/install-skype-on-ubuntu-804-hardy-heron-configure-sound/)

[http://tiny.cc/rarh3](http://tiny.cc/rarh3)

It'll probably take me a while to stumble through this, so I will write back later.

Kind regards.

OK, I went to http://tiny.cc/rarh3[/url and downloaded the file.

It is now on my Desktop, ' skype_static-2.1.0.81.tar.bz2 '

The first instruction is:-  tar -xvf skype_static-2.0.0.68.tar.bz2

Here is the result from Terminal:-

qwer@qwer-desktop:~$ tar -xvf skype_static-2.0.0.68.tar.bz2
tar: skype_static-2.0.0.68.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
qwer@qwer-desktop:~$ 

I would appreciate it if you would tell me what I did wrong?

Kind regards.

---

### Post by mikewhatever on 2010-02-08
First, you have to change to the desktop, then, the file name if different, in short:

cd Desktop
tar -xvf skype_static-2.0.0.81.tar.bz2
...
etc.

As said above, I'd first unpack the archive (right click, Extract Here), then open the unpacked folder and double clicked the executable. If it runs, it would be worth following the instructions properly.

---


---
title: "Getting MAKE command to work"
date: 2007-12-14
forum: Networking &amp; Wireless
---

### Post by rightmind on 2007-12-14
I used synaptic to load the build essentials and that came with headers it needed...i think?

I have kernel 2.6.15-29-386 in the modules folder.

I am lost here.... please give some detail on to how I can get the make command to work for me so I can install ndiswrapper -1.8.

Thank you

---

### Post by lbthrice on 2007-12-14
Hi, do you need ndiswrapper 1.8 specifically?  Because if you do not then you can get ndiswrapper 1.9 from the repository.  You may have to enable the universe repository to find it.  Try searching ndiswrapper in synaptic...if it does not show up then go settings-->repositories and enable universe.  Then search again you should see it.

if you need v1.8 specifically then you should include more information about what you have done so that people can help out.  At the minimum you should post the output of the ./configure

you can:
```
./configure > ~/Desktop/somefile.txt
```
and this will save the ./configure output to a file named somefile.txt on your Desktop...you can then cut and paste into the thread and mark it as code (see the button above the text field that looks like a hash symbol? just highlight the ./configure output and click it to format it as code) then we can see what is happening.

---

### Post by lbthrice on 2007-12-14
Whoops sorry,:oops:

 I forgot to mention tht is always good policy to let people know what version of Ubuntu you are running.

Ooops again I see that you are running Gutsy...geez...going to get some coffee

---

### Post by rightmind on 2007-12-14
My apologizes, I am running a fresh install of dapper drake, this was b4 I installed 184 updates this morning. I used synaptic package manager to install build-essentials 11.1 . I  installed the linux-kernel header 2.6.11.2-0ubuntu18.

I really just need a step buy step to get a linksys wireless adpt. wusb54g v4 to work on dapper. So, I am going from this how to here:  [http://ubuntuforums.org/showthread.php?t=192588](http://ubuntuforums.org/showthread.php?t=192588)

I cannot find the option called "settings"

---

### Post by lbthrice on 2007-12-14
Hey there,

So, I have never run Dapper but the settings menu is on the toolbar at the top of the window in synaptic in Feisty.

I wonder why you are running Dapper?  You may be surprised to find that a Feisty installation will provide native drivers for your adapter w/out ndiswrapper...but I'm not sure.  Feisty is quite nice...I actually found this to be the case for the wireles card I was using (native support wonderfully appeared with the Feisty release)

Failing the GUI 'settings' option, you can edit the /etc/apt/sources.list file instead...you can simply "uncomment" the lines in this file that contain the URLs of the repositories that you need.  May want to do this anyway because there is some useful software in these repositories that you may be interested in anyway (eg multimedia codecs).  Here's a nice tutorial:

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

For a walk-through of the ndiswrapper install, I used...

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/")

...just click the installation link...you can also find uninstall instructions here too.

Again, you may want to post the ./configure output using the method I described above so that we can see exactly what is going wrong.

One more shot in the dark for you: you may want to be sure that you are su when you run make install, if you do not run make install as su you may not have the permissions necessary to write to the directories necessary.

good luck!

---


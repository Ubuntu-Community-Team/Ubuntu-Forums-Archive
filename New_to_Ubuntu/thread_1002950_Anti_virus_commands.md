---
title: "Anti virus commands"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by Lakeside5 on 2008-12-05
Hi. A little while ago after I first installed Hardy Heron, I was given good advice on here (of course :) ) of how to run a few simple commands in the terminal to do an antivirus scan, antispyware, rootkit scan etc. I forget what it was, but suspect I might need that again, as my machine is not running as fast as it was when I first put on ubuntu (it is doing things really slow, like when I type, and surf etc., deja vu windows, so I am getting paranoid!) I would sure appreciate to run those commands again. thanks all

---

### Post by philinux on 2008-12-05
I would not worry.

Run 

top

to see if anything hogging resources.

---

### Post by hyper_ch on 2008-12-05
antivirus is not really needed

---

### Post by Lakeside5 on 2008-12-05
Excuse the dumb newb question but.. what exactly do I type in terminal? `Run`, then `top`?  Also, I just restarted the computer, and also turned my apache webserver off (have a lamp on here too) and the typing is back to normal, and generally things are normal. I still wonder about viruses though (even on linux, I`m paranoid :) Windows has left me scarred lol, battling them was an everyday war, and I lost my hard drive in the end!) 
Thanks for putting my mind at ease philinux, and hyper_ch
*edit* nm,  just typed in `sudo top` and I see everything...

---

### Post by damis648 on 2008-12-05
Just open a terminal and type
```
top
```
and press enter.

---

### Post by snova on 2008-12-05
No. Just open a terminal and type 'top', then press enter. That's how the terminal works- you type the name of a command, and it tries to run it.

I prefer 'htop', which may not be installed by default, but has a nicer interface. It's in the repositories.

---

### Post by Sealbhach on 2008-12-05
At the moment, you don't need anti-virus, there are no threats out there. This may change as Linux becomes more popular though.

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

.

---

### Post by hyper_ch on 2008-12-05
> **Sealbhach said:**
> This may change as Linux becomes more popular though.
not really

---

### Post by scorp123 on 2008-12-05
> **sealbhach said:**
> this may change as linux becomes more popular though. That's "FUD".  ):P

---

### Post by Lakeside5 on 2008-12-05
Thanks guys. damis648- off topic I know but...I just love that signature, have to share that with my friends :)

---

### Post by Gannon8 on 2008-12-05
If you _REALLY_ need antivirus (ex. hosting a downloads server and need to scan your files), there is a package called "clamav". Not exactly sure how to use it though :)

I think there is a GUI interface to it though.

---

### Post by Sealbhach on 2008-12-05
> **scorp123 said:**
> That's "FUD".  ):P

I think it's wrong to mislead people by saying that Linux is virus free. 

It's only common sense to expect that there will be more determined attacks on Linux systems as the userbase grows.


.

---

### Post by spiderbatdad on 2008-12-05
The real problems seems to be a lack of any good user friendly anti-virus software in the open source community. ClamAV is designed for scanning emails. There are several command line root kit scanners in the repos.

There is this article:[http://www.linux.com/articles/22899](http://www.linux.com/articles/22899)
A project here: [http://www.openantivirus.org/](http://www.openantivirus.org/)

If anyone knows of any AV solutions for linux, please post them. Of course cautious computer use is the first line of defense. But to say "there are no viruses in the wild" is old and bogus. It is also possible for linux servers to pass viruses on to windows machines.

---

### Post by hyper_ch on 2008-12-06
> **Sealbhach said:**
> It's only common sense to expect that there will be more determined attacks on Linux systems as the userbase grows.
Not really....

---

### Post by newbee70 on 2008-12-06
> **Gannon8 said:**
> If you _REALLY_ need antivirus (ex. hosting a downloads server and need to scan your files), there is a package called "clamav". Not exactly sure how to use it though :)

I think there is a GUI interface to it though.

there is a gui interface

go to applications

system tools

the virus scanner should be there. 

and I have found 5 windows viruses on my system, not causing me problems but would if i passed them on to a windows machine.

---

### Post by spiderbatdad on 2008-12-06
It doesn't actually come with a GUI, but this guide will show you how you can install one.[http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html](http://www.ubuntugeek.com/howto-install-clam-antivirus-with-gtk-frontend-gui.html)
Depending on your sources list, you can find it in synaptic package manager.

---

### Post by Lakeside5 on 2008-12-07
Oh, Scorp123, just got it! (ok, I had to google FUD, but learn something new everyday. Linux forums, so much more than linux...
Ooops- just noticed a few more posts since I checked this thread, so a few more people to thank! Yes, that`s a cosideration I hadn`t thought of, though it`s comforting to hear how secure linux is, I COULD pass on viruses to windows users..Even though I`m an awful noob, my intentions are to host a few websites (have been learning web design) to show what I can do, then the `client` will be given over to another hoster, but in the meantime I wouldn`t want to pass on viurses to them, wouldn`t leave a good impression lol.  I actually did install clam av on here, and someone told me before how to run it in terminal...I will check out the links and advice on here, thanks everyone.

---

### Post by grotesk on 2008-12-07
While it is somewhat accurate to say that 'there are no viruses for Linux', compromises of Linux-based systems occur extremely often. Many system compromises involve malicious software at some point or another, and using an anti-virus utility can be helpful. You may also get some mileage out of 'chkrootkit', which is also in the repositories.

Defense-in-depth is the key to security of any system, of which Anti-Virus, a strong password, and a sensible firewall policy are key components.

> **spiderbatdad said:**
> The real problems seems to be a lack of any good user friendly anti-virus software in the open source community. ClamAV is designed for scanning emails. There are several command line root kit scanners in the repos.

There is this article:[http://www.linux.com/articles/22899](http://www.linux.com/articles/22899)
A project here: [http://www.openantivirus.org/](http://www.openantivirus.org/)

If anyone knows of any AV solutions for linux, please post them. Of course cautious computer use is the first line of defense. But to say "there are no viruses in the wild" is old and bogus. It is also possible for linux servers to pass viruses on to windows machines.

---

### Post by Perfect Storm on 2008-12-07
You really don't need anti-virus on your Ubuntu. If you run a mail-server then it's a diffrent question.
Other than that those anti-virus apps you can get on Linux scans for windows viruses, so they are most likely useless in a linux as they are built for that matter. Windows viruses don't infect Linux.

1. Learn to use AppArmor which are included in Ubuntu if you feel paranoid, anything else is not needed.
2. Only use trusted sources.

That's it.

---

### Post by Paqman on 2008-12-08
> **Sealbhach said:**
> This may change as Linux becomes more popular though.


Linux is already popular. Most of the really massive internet business like Google use Linux, as does most of the hardware that runs the internet itself. If you count all the embedded linux devices like routers, TV, etc then there are probably a lot more Linux boxes in the world than Windows ones.

---

### Post by Lakeside5 on 2008-12-10
Interesting. Thanks for your comments guys :)

---


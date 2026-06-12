---
title: "Missing mencoder.conf file"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by JohnRory1971 on 2008-12-21
I want to create a profile for Mencoder so I can encode video for my Samsung YP-P2 but the mencoder.conf file is missing. i have checked in all the right places so what am I missing? I have downloaded & installed the latest version of Mencoder with Synaptic. I hope some one can help.

---

### Post by jimmy the saint on 2008-12-21
May sound obvious, but do you have hidden files visible?

---

### Post by JohnRory1971 on 2008-12-21
Yes I have I can see hidden files. I can see mplayer.conf in /etc/mplayer but mencoder.conf should be there as well and it's not:confused:. Any other ideas please?

---

### Post by jimmy the saint on 2008-12-21
```
locate mplayer.conf
```
Try typing that into the terminal and see what it kicks out.

---

### Post by JohnRory1971 on 2008-12-21
thanks Jimmy

I went to the directory / and typed:

locate mplayer.conf

It threw up nothing eventhough I can find mplayer.conf in etc/mplayer. I tried the same thing for mencoder.conf which is the missing file. Same result

---

### Post by andrew.46 on 2008-12-21
Hi,

Easiest way might be to simply create your own in $HOME:

```
$ mkdir -v $HOME/.mplayer
$ touch $HOME/.mplayer/mencoder.conf
```

Settings here will override any system settings anyway and commandline options will override both. In the man pages for mplayer there is an example mencoder.conf which demonstrates the required syntax:

>        EXAMPLE MENCODER CONFIGURATION FILE:

       # Make MEncoder output to a default filename.
       o=encoded.avi
       # The next 4 lines allow mencoder tv:// to start capturing immediately.
       oac=pcm=yes
       ovc=lavc=yes
       lavcopts=vcodec=mjpeg
       tv=driver=v4l2:input=1:width=768:height=576:device=/dev/video0:audiorate=48000
       # more complex default encoding option set
       lavcopts=vcodec=mpeg4:autoaspect=1
       lameopts=aq=2:vbr=4
       ovc=lavc=1
       oac=lavc=1
       passlogfile=pass1stats.log
       noautoexpand=1
       subfont-autoscale=3
       subfont-osd-scale=6
       subfont-text-scale=4
       subalign=2
       subpos=96
       spuaa=20


All the best,

 Andrew

---

### Post by JohnRory1971 on 2008-12-23
Thank You Andrew

Your advice worked. Can you explain the meaning of -V and also touch. I'm still learning commands

Regards
John

---

### Post by Nepherte on 2008-12-23
Check the section 'CONFIGURATION FILES" in the man page:
```
man mplayer
```

---

### Post by andrew.46 on 2008-12-23
Hi John,

> **JohnRory1971 said:**
> Your advice worked. Can you explain the meaning of -V and also touch. I'm still learning commands

Glad that is sorted out :-). The two commands I demonstrated are:

```
mkdir -v
```

The command mkdir simply creates a directory. I have added an option: -v which simply makes the command operate *verbosely*, or give more information while fulfilling the command. If you type:

```
man mkdir
```

in a terminal window you will see the details of mkdir including the use of the -v option. BTW note the difference between -v and -V, in Linux these are 2 different options.

The touch command is one that is actually used to alter or update the timestamp on a file. If the file does not exist the touch command will create it and this is commonly done as an easy method to create files. Again more details of this command can be seen by issuing the following command in a terminal window:

```
man touch
```

If you are not familiar with man pages remember that you close the page by typing 'q' without the ''. To search a man page for the text 'foo' you would type:

```
/foo
```

from within the man page and press the letter 'n' to keep searching for more matches of 'foo' within a page.

Hope this helps you?

Andrew

---

### Post by JohnRory1971 on 2008-12-24
Many thanks Andrew

John:P

---


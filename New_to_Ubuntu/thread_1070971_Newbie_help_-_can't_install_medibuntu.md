---
title: "Newbie help - can't install medibuntu"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by timpdx on 2009-02-15
I have checked for errors and typos, but for 5 times now, I type in the terminal exactly as it says in the medibuntu guide and all I get is 'no such file or directory'

Also found another command sudo wget.... from another website and it does not connect or work.

What am I doing wrong. As I said, I typed it in *exactly* as in the Intrepid 8.1 medibuntu guide.

Help! This is my first time using the terminal, so I may be doing something wrong?

---

### Post by RomeReactor on 2009-02-15
Hi Which guide are you following? Please post the commands you used.

---

### Post by diablo75 on 2009-02-15
```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Copy and paste the above code into a terminal window and that will add the software sources to your system.  You can then use the terminal or Synaptic Package Manager to add whatever medibuntu related packages to your PC, such as the libdvdcss2 package (for DVD playback).

---

### Post by timpdx on 2009-02-15
I opened terminal, used the command at medibuntu.org:

```
sudo wget http://www.medibuntu.org/sources.list.d/intrepid.list--output-document=/etc/apt/sources.list.d/medibuntu.list
```

---

### Post by RomeReactor on 2009-02-15
As posted above those are the instrucions you should be following (here's the complete [Community Documentation guide for Medibuntu]("https://help.ubuntu.com/community/Medibuntu"))

---

### Post by timpdx on 2009-02-15
> **RomeReactor said:**
> As posted above those are the instrucions you should be following (here's the complete [Community Documentation guide for Medibuntu]("https://help.ubuntu.com/community/Medibuntu"))

oh well, I tried, I still can't watch a movie because my gstreamer is missing a plug in.

Also tried VLC, no luck getting a movie to play.

---

### Post by timpdx on 2009-02-15
> **timpdx said:**
> oh well, I tried, I still can't watch a movie because my gstreamer is missing a plug in.

Also tried VLC, no luck getting a movie to play.

VLC ***is*** working now, but movie player wants the gstreamer plug in still. But VLC is good enough.

---

### Post by RomeReactor on 2009-02-15
> **timpdx said:**
> VLC ***is*** working now, but movie player wants the gstreamer plug in still. But VLC is good enough.

Try installing the **ubuntu-restricted extras** package, which will add some codecs to your media players.

---

### Post by kansasnoob on 2009-02-15
So, did you get the Medibuntu thing straightened out or not?

If you think so but aren't sure go to terminal and run:

```
sudo apt-get update
```

If the terminal spits back errors we'll know what to do.

As far as gstreamer there are two ways to go:

#1: Go to synaptic and type gstreamer into the search window. Tick everything beginning with gstreamer for installation! Actually you can skip the documentation and development files, but they don't break anything, and it can be difficult deciding what is or is not dev or doc!

#2: In terminal run:

```
sudo apt-get install gstreamer*
```

But then you'll be dogged to buy 2 fluendo-plugins packages until you go to synaptic and "untick" them. 

I do wonder if you've even installed ubuntu-restricted-extras?

---

### Post by timpdx on 2009-02-15
> **RomeReactor said:**
> Try installing the **ubuntu-restricted extras** package, which will add some codecs to your media players.

I tried that, it never worked, it says there are conflicts.

---

### Post by RomeReactor on 2009-02-15
> **timpdx said:**
> I tried that, it never worked, it says there are conflicts.

Please post you sources.list:
```
cat /etc/apt/sources.list
```

---

### Post by timpdx on 2009-02-15
> **RomeReactor said:**
> Please post you sources.list:
```
cat /etc/apt/sources.list
```

"no such file exists" (I assume that I do the cat command in terminal)

Ubuntu isn't easy for the lay person, I can't even watch youtube (d/l adobe flash AND the gnu flash (gnash) player with NO luck)

---

### Post by RomeReactor on 2009-02-15
Try:
```
ls /etc/apt
```
and post back the result.

Are you sure you entered the command correctly? The file *should* be there. When one's not used to the terminal, it's easier to copy and paste these commands there.

---

### Post by oldos2er on 2009-02-15
> **timpdx said:**
> "no such file exists" (I assume that I do the cat command in terminal)

Ubuntu isn't easy for the lay person, I can't even watch youtube (d/l adobe flash AND the gnu flash (gnash) player with NO luck)

 Please copy and paste
```
ls /etc/apt
```
into a terminal, and post the output here.

---


---
title: "trouble with movie player"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by tegdirb on 2010-08-05
Hi everyone,

I have just installed Ubuntu 10.04, but feel a bit lost trying to play a DVD on my computer. Movie Player says it cannot find the plugins suitable to make it work. Sorry, but I'm a beginner so I'm not sure what I can do to watch a movie- something that seemed to work so easily in the earlier version.. :-/ (sniff)
Any help for a beginner like me?
Thanks a lot in advance  ;)

---

### Post by cariboo on 2010-08-05
The proper codecs to play DVD's are not installed by default due to legal reasons. There are couple of ways to get the proper codec.

[list=1]
[*] Enable the Medibunti repositories, download and install libdvdcss2. Go [here]("https://help.ubuntu.com/community/Medibuntu") and follow the instructions on how to enable the repositories. Then go to either the Software Center or Synaptic package manager and search for libdvdcss2 and mark it for installation.

[*] Install libdvdcss2 manually. Go to either The Software Center or Synaptic Package Manager and install the ubuntu-restricted-extras meta package, then open a terminal and navigate to /usr/share/doc/libdvdread4 then type:

```
sudo ./install-css.sh
```

The above command will automagically install libdvdcss2

[*] Insert dvd in drive and enjoy.

[/list]

---

### Post by tegdirb on 2010-09-05
Thanks so much for your help! Seems to have solved the problem!

Cheers! ;-)

---

### Post by mike0liver on 2010-09-05
> **cariboo907 said:**
> The proper codecs to play DVD's are not installed by default due to legal reasons. There are couple of ways to get the proper codec.

[list=1]
[*] Enable the Medibunti repositories, download and install libdvdcss2. Go [here]("https://help.ubuntu.com/community/Medibuntu") and follow the instructions on how to enable the repositories. Then go to either the Software Center or Synaptic package manager and search for libdvdcss2 and mark it for installation.

[*] Install libdvdcss2 manually. Go to either The Software Center or Synaptic Package Manager and install the ubuntu-restricted-extras meta package, then open a terminal and navigate to /usr/share/doc/libdvdread4 then type:

```
sudo ./install-css.sh
```

The above command will automagically install libdvdcss2

[*] Insert dvd in drive and enjoy.

[/list]
Hi:
 
I have a similar problem but I can't find the ubuntu-restricted-extras meta package anywhere so I can install it. I don't have libdvdread4 in the directory /usr/share/doc/ and am not sure how to get hold of that item. I am running Ubuntu 10.04 as is "tegdirb" above and am trying to play "The Matrix" DVD.
 
Can you point me in the right direction, please (I am non-technical).
 
Thanks,
 
Mike

---

### Post by 3rdalbum on 2010-09-05
> **mike0liver said:**
> Hi:
 
I have a similar problem but I can't find the ubuntu-restricted-extras meta package anywhere so I can install it.

Reload your package list - go to System > Administration > Synaptic Package Manager and click Reload.

---


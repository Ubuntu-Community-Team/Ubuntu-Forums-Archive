---
title: "Password error"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by maspiotis on 2007-02-18
I was screwing around with commands in the terminal last week trying to get midi files to play, when I encountered the following problem.  I would type in my password from the terminal and then the terminal crapped out on me and there was no prompt.  

Now everything seems fine at the terminal with my password and the computer recognizes my password when I boot up, but I went to synaptic today and after entering my password I got the following error:

E: Type 'mypassword' is not known on loine 34 in source list/etc/apt/sources.list

E: The list of sources could not be read go to the repository dialogue to correct the problem

I am running edgy on a sony vaio laptop

Thanks for any help

Michael Aspiotis

---

### Post by Reedbeta on 2007-02-18
Sounds like the sources.list file got borked somehow.  Try doing 'sudoedit /etc/apt/sources.list' - go to line 34 and see what the problem is, hopefully it should be fairly obvious how to correct it.

---

### Post by maspiotis on 2007-02-19
Okay, I did that and got this:           is there anything out of order here?




 GNU nano 1.3.12       File: /var/tmp/sources.list.XX6sp0K4          Modified  


deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiver$
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe mult$

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe $
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted unive$

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

                               [ Read 70 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---


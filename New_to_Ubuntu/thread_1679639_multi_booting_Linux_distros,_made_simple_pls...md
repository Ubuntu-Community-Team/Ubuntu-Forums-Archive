---
title: "multi booting Linux distros, made simple pls.."
date: 2011-02-01
forum: New to Ubuntu
---

### Post by heron7 on 2011-02-01
I am trying to partition my  .Hdrive ,using the sys rescue cd but  gparted does not allow me or rather the sub context menu 'resize' option  is not available. 
 The resue cd runs off the ram from the cd tray which it ejects.
i have fedora14 on & it reads LVM . this is normally my external  drive but to make it easier i removed Ubuntu's Drive  (cheat)..&  placed the fedora as to avoid accidents on my Ubuntu. 
 I've been trying to edit the grub.config OR menu.lst for 'shamefully'  over two weeks ,read countless ways of 'multi booting LINUX not Windows  & i'm still nowhere. 
'Chainloading' I'm stuck in the part where i either decide to purge  grub2 or NOT ! find a startup manager which if i understood will make  the option of choosing the os ,edit menu.lst  ' set the MBR with grub's  Leg ?..or wait till 11.04 :guitar:
 by the way guys ,i had a peak back at 9.04 ystrdy & i have saw that  Ubuntu always worked fine but yet so many are busy everyday improving  ..amazing really. That's what i like about open source ,some many  dedicated people involved in constant; maintenance is allready alot of  work ,yet you find room for speedy evolution which effects whole of  society:KS

editing the menu?... find the menu.lst by activating show hidden files   from nautilus,then ... use gedit to enter extra 3lines :( somewhere  around the third paragraph :( or at the end ?... title 
      rootnoverify  ?...
      ??....
 there's grub to be either purged or edited , vai text editor ,konsole , & grub menu boot too? which is where my keyboard keys change to qwerty & get stuck trying to enter the    grub> root (hd0,0) .. etc ..
   i have now managed with bt4 on live environment & from there too Gparted says fed is lvm & locked , only formatting option available, but how do i make way ,??.. give fedora14 50Gb & place Bt4 on the same drive ,booting both choosing at startup.?

I gave up trying this on external drive & i'm starting to miss Ubuntu after a day with my laptop bottom uncovered & wind coming out it :lolflag:  help 
 :mad:            OR ...                                                      ):P

---

### Post by heron7 on 2011-02-01
I just realized that i had left the post... and gone back to try with Bt4 . 
 no longer have rescue cd in the drive bay ,ofcoarse Bt4 is on now.

---

### Post by jjex22 on 2011-02-01
Sorry I got a little confused, are you trying to triple boot fedora ubuntu and backtrack from the same drive?

Could you give a list of which opertating systems and distros you would like to have on each physical drive?

Many thanks

---

### Post by ajgreeny on 2011-02-01
I am also confused and have no idea what, if anything, you have wortking on the machine at the moment.

In general terms, if you have a working grub2 at the current time, I suggest you put grub from all the still to be installed OSs onto their own root partitions, and then run **sudo update-grub**, or just **update-grub** as root, if you don't already have a ubuntu family supplying grub.  That will allow grub to find and add the newly installed linux distros to the grub menu.

However, more info please, about where you are at the moment, and where you want to be.

---

### Post by heron7 on 2011-02-01
Sorry guys ,i said i had stopped with posting the help , copied the post  ,went off and removed the rescue cd and placed Bt4 ... then still in the same predicament i came back and pasted the first mess and started ranting , ehhmm .. from where i then was .. 
Anyways there are three os i can access the actual drive from. of caoarse one at a time , only because i know that fedora has yum and Bt4 has sudo & that's why i mentioned both . 

so NOW there's bt4 on live enviroment and fedora asleep ,;lol ... 
 fedora reads LVM  i wat to take some of that 45000 ytes and make room for bt4 which is etx3 format..;

---

### Post by scarey9 on 2011-02-01
Have you tried Booting with the Fedora Live CD and using the Partition manager on that?

---


---
title: "Please help!! No web browser!!"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by Dommi35 on 2010-03-13
[FONT=Arial][SIZE=3][COLOR=darkred]**Hi**[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=3][COLOR=darkred]**I have an asus pc 4G with linux. I know hardly anything about linux except how to open console window and use konqueror. My firefox needed updating so i googled and followed online instructions to install version 3 over my old version. However then I had problems as it said I need GTK+ 2.10.**[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=3][COLOR=darkred]**i downloaded this but have NO idea where to install it to! :confused:**[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=3][COLOR=darkred]**I researched online and it appears that it might not end with needing to upgrade GTK +. People say a new OS may be needed! So what do i do?**[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=3][COLOR=darkred]**PLUS..I currently have NO web broswer as I killed my old firefox. :frown:**[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=3][COLOR=darkred]**Is there a OS update which would help? Should I re-install and older firefox? If so which version? Or is there an alternative web browser I could use?**[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=3][COLOR=darkred]**Please help as I am at a dead end.... ](*,)**[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=3][COLOR=darkred]**Worth mentioning this ASUS only has about 400mb free HD (out of 4 gig) and netbook says:**[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=3][COLOR=darkred]**LINUX eeepc-user 2.6.21.4 eeepc**[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=3][COLOR=darkred]**i686 GNU/Linux**[/COLOR][/SIZE][/FONT]
 
[FONT=Arial][SIZE=3][COLOR=darkred]**Look forward to hearing from you! ;)**[/COLOR][/SIZE][/FONT]

---

### Post by MichealH on 2010-03-13
Just follow this link It should install straight away [firefox(apturl will install this)]("apt://firefox")

---

### Post by _h_ on 2010-03-13
> **MichealH said:**
> Just follow this link It should install straight away [firefox(apturl will install this)]("apt://firefox")

And if the apturl doesn't want to work for you, you can get Firefox via Synaptic (System -> Administration -> Synaptic Package Manager).

---

### Post by arochester on 2010-03-13
Q. Is there something in the OP to suggest that it is Ubuntu or a derivative? Eeepcs commonly use Xandros...

---

### Post by aysiu on 2010-03-13
It doesn't sound to me as if you're using Ubuntu Linux.

It sounds as if you're using the Xandros Linux that came with the Eee PC. Software installation on that version of Xandros is extremely difficult and annoying.

My advice would be to do one of three things: [list=1][*]Install Firefox 3 using [=firefox"]this tutorial]("http://wiki.eeeuser.com/howto:installfirefox3?s[). I couldn't find any info on installing Firefox 3.5 or 3.6 on the Eee PC.[*]Reinstall Firefox 2 on your Eee, which you can do by pressing Control-Alt-T and then pasting in the command ```
sudo apt-get update && sudo apt-get install firefox
```[*]Install Ubuntu instead[/list] I used to have an Eee PC 701, and Ubuntu takes longer to boot up on it than Xandros, but it is **much** easier to use, and it's a lot easier to [get the latest Firefox installed](http://ubuntuzilla.sourceforge.net) on, too.

---

### Post by Dommi35 on 2010-03-13
**[SIZE=4][COLOR=darkred]oooh!![/COLOR][/SIZE]**
**[SIZE=4][COLOR=darkred]You were all very quick!![/COLOR][/SIZE]**
**[SIZE=4][COLOR=darkred][/COLOR][/SIZE]** 
**[SIZE=4][COLOR=darkred]Thanks everyone..off to try out some of these things...[/COLOR][/SIZE]**
**[SIZE=4][COLOR=darkred]will be reporting back asap[/COLOR][/SIZE]**
**[SIZE=4][COLOR=darkred](hopefully with a success story)  ;)[/COLOR][/SIZE]**

---

### Post by Dommi35 on 2010-03-13
Hi Aysiu
re: points 1,2 & 3

1.this didn't work. I tried several times. Spent ages on it!I dont have a usr folder in my gtk2 folder..is this why?
2. I tried reinstalling firefox 2 but  it keeps saying i have the latest version already. I am going to try again...
3. Although this is tempting I am nervous I will mess this up as I am rather clueless! At the moment by asus has a system restore facility which is my safegaurd. Since I am a mega novice would installing ubuntu be safe in my hands?!
 
_________________________________________________________
 
Hi Michael, where is (System -> Administration -> Synaptic Package Manager). ??

---

### Post by aysiu on 2010-03-13
> **Dommi35 said:**
> Hi Aysiu
re: points 1,2 & 3

1.this didn't work. I tried several times. Spent ages on it!I dont have a usr folder in my gtk2 folder..is this why? Who knows? I tried to stick with the stock Xandros Eee as long as I could, but little niggles like this kept annoying me. > 2. I tried reinstalling firefox 2 but  it keeps saying i have the latest version already. I am going to try again... It's probably installed then. Maybe just the icon is gone or not working? Can you press Control-Alt-T and then paste in the command ```
firefox &
``` and see if it launches? And, if not, can you paste the resultant error message back here? > 3. Although this is tempting I am nervous I will mess this up as I am rather clueless! At the moment by asus has a system restore facility which is my safegaurd. Since I am a mega novice would installing ubuntu be safe in my hands?! Certainly a legitimate concern. I think a good place to start would be "burning" a Ubuntu image (it's a large file with a .iso extension) to a USB stick with <a href="http://unetbootin.sourceforge.net">UNetBootIn</a> and then trying Ubuntu out without installing it (that's the default behavior when you boot from the live CD... or live USB, in this case). If you like the live Ubuntu and have played around with it enough to be comfortable, we can help you back up your Eee installation fully before you try a full Ubuntu installation. You definitely don't have a big enough SSD to do a dual-boot! > Hi Michael, where is (System -> Administration -> Synaptic Package Manager). ?? Michael is probably assuming you're using Ubuntu (since this is the Ubuntu Forums, after all). If you're using Xandros (the Linux that comes with the Eee PC), press Control-Alt-T and then paste in the command ```
kdesu synaptic
```

---

### Post by Dommi35 on 2010-03-13
**[SIZE=2][COLOR=purple]ALL SORTED!! =D>[/COLOR][/SIZE]**
**[SIZE=2][COLOR=purple][/COLOR][/SIZE]** 
**[SIZE=2][COLOR=purple]I used [/COLOR][/SIZE]****[SIZE=2][COLOR=purple]Using a simple script[/COLOR][/SIZE]****[SIZE=2][COLOR=purple] from the EEEuser website Aysiu posted..[/COLOR][/SIZE]**
**[SIZE=2][COLOR=purple]for some bizzare reason I was trying it the harder way using the advanced method (I hadn't seen my netbook model listed in the easy bit)[/COLOR][/SIZE]**
**[SIZE=2][COLOR=purple]I now have FIREFOX 3!![/COLOR][/SIZE]**
**[SIZE=2][COLOR=purple][/COLOR][/SIZE]** 
**[SIZE=2][COLOR=purple]Will consider updating to ubuntu tho' as I dont want this agro again..[/COLOR][/SIZE]**
**[SIZE=2][COLOR=purple][/COLOR][/SIZE]** 
**[SIZE=2][COLOR=purple]thank you sooooo much!!![/COLOR][/SIZE]**
**[SIZE=3][COLOR=purple]You are stars![/COLOR][/SIZE]**
 
:KS

---


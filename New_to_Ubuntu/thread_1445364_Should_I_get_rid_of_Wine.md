---
title: "Should I get rid of Wine?????"
date: 2010-04-02
forum: New to Ubuntu
---

### Post by @rizz on 2010-04-02
Hi Guys,

  I have Wine installed on my computer on my computer. and what ever software that i try to install gets installed without a problem. 
  However None of them works. some opens up but gets hanged and the rest doest event open up on the screen.

 Now i am quite happy with what ever software i have on Linux, so i ask you my friends 
should i remove Wine from my computer....???????

---

### Post by Chesamo on 2010-04-02
Why bother having it if you don't use it?

---

### Post by tooatw on 2010-04-02
> **@rizz said:**
> Hi Guys,

  I have Wine installed on my computer on my computer. and what ever software that i try to install gets installed without a problem. 
  However None of them works. some opens up but gets hanged and the rest doest event open up on the screen.

 Now i am quite happy with what ever software i have on Linux, so i ask you my friends 
should i remove Wine from my computer....???????

the only thing i keep wine for is utorrent

---

### Post by @rizz on 2010-04-02
Does utorrent work for u through wine? .....i can't seem to get anything to work through it.

I use transmission. its great!

---

### Post by Chesamo on 2010-04-02
This might help you.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824)

---

### Post by haddog on 2010-04-02
I say keep wine. You just have to go through some trial and error. Once you do get it workin it's great.

I use wine to use a bible study program called e-Sword that is windows based. I have been able to install all the modules in e-Sword via wine just like on a windows PC.

---

### Post by haddog on 2010-04-02
> **Chesamo said:**
> This might help you.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824)


And this has helped me:

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

---

### Post by achase79 on 2010-04-02
> **Chesamo said:**
> This might help you.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6824)

+1

When using Wine, if you have problems always check the AppDB at winehq.org for any reported issues or workarounds.  PlayOnLinux is a good companion for Wine that it has installation assistance and configuration assistance for specific programs.

---

### Post by ibuclaw on 2010-04-02
If you have no use for Windows applications on Linux, there is no need for WINE. :)

---

### Post by conradin on 2010-04-02
I cant see the reason behind wine. Every app that it will run has a equivalent linux alternative. Some one said utorrent? Use transmission, it runs native.

---

### Post by Rushyang on 2010-04-02
Hey guys, I had a quick question...

If [rizz]("http://ubuntuforums.org/member.php?u=1046663") removes WINE from his computer then, all space occupied by windows applications will be freed too?

---

### Post by lavinog on 2010-04-02
> **Rushyang said:**
> Hey guys, I had a quick question...

If [rizz]("http://ubuntuforums.org/member.php?u=1046663") removes WINE from his computer then, all space occupied by windows applications will be freed too?

No, they reside in ~/.wine which shouldn't get removed just because you removed wine.

---

### Post by Chesamo on 2010-04-02
Though theoretically sudo apt-get purge wine *should* remove the ~/.wine directory, but I know it doesn't.

The easiest way to free the space is to run the Purge above, then rm -r ~/.wine to delete the directory.

---

### Post by arnab_das on 2010-04-02
> **@rizz said:**
> Hi Guys,

  I have Wine installed on my computer on my computer. and what ever software that i try to install gets installed without a problem. 
  However None of them works. some opens up but gets hanged and the rest doest event open up on the screen.

 Now i am quite happy with what ever software i have on Linux, so i ask you my friends 
should i remove Wine from my computer....???????

sometimes using a different version of wine can work wonders for u. eg. the latest release of wine is 1.1.41. however none of the windows games i have run on it. i have since then 'downgraded' to 1.1.31 where all those games work near perfectly. if a particular version isnt working for u, i would suggest u go through the other versions as well.

also you should check out the wine app database to see if ur application is included in the ones which are sort of 'wine compatible'. [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by ibuclaw on 2010-04-02
> **Chesamo said:**
> Though theoretically sudo apt-get purge wine *should* remove the ~/.wine directory, but I know it doesn't.


You can not be more wrong in your theory. ;)

purge removes configuration files associated with the package in the /etc directory.

User configuration is not touched.

Regards
Iain

---

### Post by @rizz on 2010-04-02
Hey Thanks for the replies now

 i decided to to reinstall a different version of wine(i had 1.2....quite old you might say;))

but now i did uninstall using the sudo  apt-get --purge and stuff command and even deleted the ~/.wine directory

but my applications menu still shows wine listed there...?? though most of the options are gone!!!

now i will probably reinstall it again but would like to know if the sofware and the main directory is removed why is it still there on the menu?

any ideas?

---

### Post by arnab_das on 2010-04-02
> **@rizz said:**
> Hey Thanks for the replies now

 i decided to to reinstall a different version of wine(i had 1.2....quite old you might say;))

but now i did uninstall using the sudo  apt-get --purge and stuff command and even deleted the ~/.wine directory

but my applications menu still shows wine listed there...?? though most of the options are gone!!!

now i will probably reinstall it again but would like to know if the sofware and the main directory is removed why is it still there on the menu?

any ideas?

i know what ur problem is.

[http://exploreubuntu.wordpress.com/2010/01/15/remove-programs-from-wine/](http://exploreubuntu.wordpress.com/2010/01/15/remove-programs-from-wine/)

follow the instructions there. pretty simple.

---

### Post by @rizz on 2010-04-03
Hey thanks Arnab, it worked! now i will try and re install a different version of wine...

---

### Post by haddog on 2010-04-03
> **@rizz said:**
> Hey thanks Arnab, it worked! now i will try and re install a different version of wine...

Don't give up, let us know your results and what you did. Wine is a beautiful thing when it works. Taste good too!

---

### Post by sandyd on 2010-04-03
> **@rizz said:**
> Hey thanks Arnab, it worked! now i will try and re install a different version of wine...
[URL="http://www.winehq.org/download/deb"]http://www.**wine**hq.org/download/**deb**
[/URL] ;)

---


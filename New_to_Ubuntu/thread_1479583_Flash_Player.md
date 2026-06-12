---
title: "Flash Player?"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by mclizardman24 on 2010-05-10
Hi, I just started using Ubuntu Linux using a dual boot with windows 7, and am having some problems with flash. I used the synaptic package manager to install it nad made sure all my drivers were up to date by using the ones that were recommened to me on the desktop, but when I play flash games, the screen flickers, and lags, adn is really glitchy. What can i do for this?

---

### Post by ubunterooster on 2010-05-10
Are you using 64-bit Ubuntu with 64 bit flash ( default for 64-bit is 32-bit flash which causes errors)

---

### Post by mclizardman24 on 2010-05-10
> **ubunterooster said:**
> Are you using 64-bit Ubuntu with 64 bit flash ( default for 64-bit is 32-bit flash which causes errors)
 
Erm, honestly i dont know. im using 7 now, and its been awhile since i downloading it from the ubuntu site. it could be 64 bit. How do i check?

---

### Post by ubunterooster on 2010-05-10
type "uname -a" in the terminal.

 Mine is 64-bit so I get ```
ubunterooster@Rooster:~$ uname -a
Linux Rooster 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 [color=red]x86_64[/color] GNU/Linux
ubunterooster@Rooster:~$ 
```Color is used to highlight important part

---

### Post by sandyd on 2010-05-10
if you get x86_64, see my signature. otherwise, ignore this post.

---

### Post by mclizardman24 on 2010-05-10
> **ubunterooster said:**
> type "uname -a" in the terminal.

 Mine is 64-bit so I get ```
ubunterooster@Rooster:~$ uname -a
Linux Rooster 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 [COLOR=red]x86_64[/COLOR] GNU/Linux
ubunterooster@Rooster:~$ 
```Color is used to highlight important part
  This is what i got

Linux ubuntu 2.6.31-20-generic-pae #58-Ubuntu SMP Fri Mar 12 06:25:51 UTC 2010 i686 GNU/Linux

---

### Post by ubunterooster on 2010-05-10
So you are 32-bit...

I hope some one comes along shorty with more info than I have, but in the meantime it appears you may want to update and then go to System>Administration>Time and Date. Click on the padlock give your password, and under configuration, select "keep synchronized with internet servers". (Unless you have a reason for it being as it is)

---

### Post by mclizardman24 on 2010-05-10
> **ubunterooster said:**
> So you are 32-bit...

I hope some one comes along shorty with more info than I have, but in the meantime it appears you may want to update and then go to System>Administration>Time and Date. Click on the padlock give your password, and under configuration, select "keep synchronized with internet servers". (Unless you have a reason for it being as it is)

Well, so do I, lol. i was thinking about building a computer but didnt want to pay for an os and i have this cd laying around anyway, so why not use it? I hope someone figures this out.

---

### Post by sandyd on 2010-05-10
try the below
```

sudo apt-get remove --purge flashplugin-installer flashplugin-nonfree adobe-flashplugin
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc4_linux_050510.tar.gz
sudo rm /usr/lib/mozilla/libflash*
sudo tar xvfz flashplayer10_1_rc4_linux_050510.tar.gz -C /usr/lib/mozilla/plugins

```p.s. did you install your graphics drivers?
go to system -> administration -> hardware drivers
and see if theirs any there you can use.

---

### Post by 3rdalbum on 2010-05-10
If you have an ATI graphics card, try disabling Desktop Effects. ATI's graphics driver doesn't really play nice.

---

### Post by mclizardman24 on 2010-05-11
> **carlee said:**
> try the below
```

sudo apt-get remove --purge flashplugin-installer flashplugin-nonfree adobe-flashplugin
wget -c http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_1_rc4_linux_050510.tar.gz
sudo rm /usr/lib/mozilla/libflash*
sudo tar xvfz flashplayer10_1_rc4_linux_050510.tar.gz -C /usr/lib/mozilla/plugins

```p.s. did you install your graphics drivers?
go to system -> administration -> hardware drivers
and see if theirs any there you can use.
 
Okay, yeah I'll try that. Its to uninstall right? And I have all my drivers up to date according to Ubuntu at least.(And I have a geforce 9400gt for above) Oh yeah, at the beginning i forgot to mention that the sound also is about 2 seconds behind everything when i do flash stuff.

---

### Post by sandyd on 2010-05-11
did you ever fiddle with ~/.asoundrc or /etc/asound.conf by any chance?

If you did (like me) it is likely the cause...

---

### Post by Cavsfan on 2010-05-11
I found this site that explains how to update your java.
32 bit instructions on the left side and 64 bit instructions on the right.
(32 bit/64 bit machine not 32/64 bit java)
If you do exactly as this says, you will have the latest version of java.
It says to just modify it for the different version of java, but they usually keep it up to date already.
I've used it a few times with great results.

[U][COLOR=Blue][Easy Java Update Instructions]("http://sites.google.com/site/easylinuxtipsproject/java")

[/COLOR][/U][COLOR=Black]EDIT: [/COLOR][COLOR=Black]I didn't mean to butt in, but these instructions make this task so easy.[/COLOR][U][COLOR=Blue]
[/COLOR][/U][COLOR=Blue][COLOR=Black]Then you just google "java version test" to verify the update.[/COLOR][/COLOR][U][COLOR=Blue]
[/COLOR][/U]

---

### Post by mclizardman24 on 2010-05-11
> **carlee said:**
> did you ever fiddle with ~/.asoundrc or /etc/asound.conf by any chance?

If you did (like me) it is likely the cause...

I don't recall, no. Don't even know what those are, lol.

---


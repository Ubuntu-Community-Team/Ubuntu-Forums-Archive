---
title: "Wireless help with Atheros card!!!"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by AmanoAcid on 2008-02-19
HI everyone...

I recently switched to Ubuntu after vista crashed on me.. and I don't want to go back to vista, we all know it sucks

I have an Acer Aspire 5570z notebook, and it has an Atheros wireless card, i believe it is a AR5007EG..

well my computer stopped recognizing it after I installed ubuntu 7.04.. I have viewed other "solutions" for my same problem.. they either didn't work, or i didn't understand the directions!

I tried something with ndiswrapper, and it seemed to change something.. In the "restricted drivers" in system>administration, it no longer has an error next to the "Atheros Hardware Layer Access (HAL)".. it just simply has a checkmark under 'enabled', then the status says 'not in use'.. why is it not in use?

so any help with getting ubuntu to recognize my card? and I should add.. I am a complete newb to ubuntu so detailed instructions would help!

Thanks in advance!

---

### Post by Hightide on 2008-02-19
HI AmanoAcid

This [thread ]("http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html")may help.

regards

:)

---

### Post by AmanoAcid on 2008-02-22
Thanks, it works perfectly now!

one problem though.. after turning off the computer and returning to it the next day, the wireless problem returned, and I had to type all those codes in the terminal again

any way to make it so I don't have to repeat this process at every start up?

---

### Post by RSLxH on 2008-02-22
> **AmanoAcid said:**
> Thanks, it works perfectly now!

one problem though.. after turning off the computer and returning to it the next day, the wireless problem returned, and I had to type all those codes in the terminal again

any way to make it so I don't have to repeat this process at every start up?

Just echo it to the modules file. It should then load ath_pci at boot:

```
modprobe ath_pci
``````
echo ath_pci >> /etc/modules
```

From my Howto:
[http://dreamlinuxforums.org/index.php/topic,55.0.html](http://dreamlinuxforums.org/index.php/topic,55.0.html)

---

### Post by AmanoAcid on 2008-02-22
^nothing happened when I typed those codes into the terminal...

the first one gave me a fatal error, second one said permission denied..

maybe I'm doing something wrong? what do you mean by 'echo it into the modules file'?

---

### Post by AmanoAcid on 2008-02-23
anyone?

---

### Post by AmanoAcid on 2008-02-24
Please anyone? I believe it is real simple to have this work on start up but I don't know how to do it

---

### Post by RSLxH on 2008-02-24
> **AmanoAcid said:**
> Please anyone? I believe it is real simple to have this work on start up but I don't know how to do it

Ok, change to root first by issuing the su command + password, then repeat the commands in my previous post.

---

### Post by AmanoAcid on 2008-02-25
I get this message when I put " echo ath_pci >> /etc/modules" in the terminal:


bash: /etc/modules: Permission denied


and that su command won't take my pass? and I know I'm using the right password... it says:

su: Authentication failure
Sorry.


? yea I'm an absolute newb wit this so.. is there something I'm doing wrong?

---

### Post by Junglizer on 2008-02-25
type ```
su - 
``` into the terminal. It will prompt you for your root password, once you put this in you should have sufficent privliges to complete the previously posted commands.

---

### Post by RSLxH on 2008-02-25
> **AmanoAcid said:**
> I get this message when I put " echo ath_pci >> /etc/modules" in the terminal:


bash: /etc/modules: Permission denied


and that su command won't take my pass? and I know I'm using the right password... it says:

su: Authentication failure
Sorry.


? yea I'm an absolute newb wit this so.. is there something I'm doing wrong?

Did you set a root passwd? If not you can set/change it with:
```
sudo passwd root
```
Just enter the password twice and that is your root password set.

If you can't sudo, it's because you aren't listed in the sudoers file. You should change it with Vi or Vim text editors using vsudo, but you can also add it with nano:
```
su
```
then enter your password to become root.

then:
```
nano /etc/sudoers
```

Scroll down to where it says:
```
# User privilege specification
root    ALL=(ALL) ALL

```

and add your username:
```
# User privilege specification
root, junglizer    ALL=(ALL) ALL

```

Now hit **Ctrl + X** to exit
Type **y** to save
and **Enter** to get back to the terminal.

Now you can su, sudo, kdesu, gksu etc.

---


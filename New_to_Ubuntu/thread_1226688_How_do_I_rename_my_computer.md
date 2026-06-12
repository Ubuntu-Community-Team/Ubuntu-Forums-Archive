---
title: "How do I rename my computer?"
date: 2009-07-29
forum: New to Ubuntu
---

### Post by zer010 on 2009-07-29
How do I rename my computer?

---

### Post by connorh123 on 2009-07-29
Not sure what you're trying to ask.
Elaborate please.

---

### Post by theozzlives on 2009-07-29
```
gksu gedit /etc/hosts
gksu gedit /etc/hostname
```

---

### Post by LookTJ on 2009-07-29
how do you change your hostname?

Try this:
```
sudo /bin/hostname mynewhostname
```replace "myhostname" with your desired name.

:)

Also, change it here too:
```
sudo edit /etc/hosts
```

---

### Post by zer010 on 2009-07-30
whenever you install Ubuntu, on the second to last step, you put in your name and password and after that you name the computer.  Default is usually something like "username@desktop" .  I mistyped the name I wanted and didnt catch it until I went into the terminal. How do I correct this with out reinstalling?

---

### Post by starcannon on 2009-07-30
If you would like to rename your computer using a GUI:

Menu:
System>Administration>Network: 

Click on "Unlock" bottom middle right of window.
Enter Password

Click on the General tab:
In the "Host name" text field change the name to what you want.

Click Close

Reboot.

---

### Post by zer010 on 2009-07-31
Thanks!!  I knew it could be done, but I just didn't know where to look. Thanks for all the help!
==================================================================
OOps!! I spoke too soon!! I couldn't find what you (starcannon) were talkin about. All I have related to network in Sys>Admin is network tools. Ping, whois, etc..  Sys>Pref has Network Connections, but that doesnt have what you were talkin bout either.  I am using jaunty by the way.

---

### Post by llamabr on 2009-07-31
Yes, seems like a small thing, to warrant a reinstall.

If you just want to adjust the bash prompt in the terminal, you need to change your PS1 settings:

[http://www.google.com/search?q=ps1+bashrc&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=ps1+bashrc&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

(sorry, I couldn't find a more specific howto, but there are plenty here).

---

### Post by jerome1232 on 2009-07-31
Two people gave the commands to get it changed earlier in the thread. Ubuntu switched to a new network manager in 8.04 I believe and it does not yet have the ability to change the hostname from a gui.

---

### Post by zer010 on 2009-08-01
Ok, terminal here I come! I don't mean to be rude, especially to someone helping me out but, in you're signature, it's  'lobbed a sword'. I LOVE that line! One of my fav's.  Also, 'Led by a bottle more like!' Makes me want to watch it again!

---

### Post by jerome1232 on 2009-08-01
I'll have to fix my sig lol! I haven't seen that movie in awhile.

---

### Post by zer010 on 2009-08-01
I followed LookTJ's code and it seemed to work. however, when i open up the terminal, its still same as before.  im sure i can change it as far as the "command leader", but where ever file the leader is origionally getting its info must not have been changed. how do i fix that ? llamabr said to fix PS1 settings, where and how do i do that? Plz help before i restall for the 107th time!

---

### Post by LookTJ on 2009-08-01
> **zer010 said:**
> I followed LookTJ's code and it seemed to work. however, when i open up the terminal, its still same as before.  im sure i can change it as far as the "command leader", but where ever file the leader is origionally getting its info must not have been changed. how do i fix that ? llamabr said to fix PS1 settings, where and how do i do that? Plz help before i restall for the 107th time!May you provide the info of /etc/hosts?

```
cat /etc/hosts
```
To edit:```
sudo gedit /etc/hosts
```also please provide:
```
echo $PS1
```:)

---

### Post by zer010 on 2009-08-03
Well, I tried [LookTJ]("http://ubuntuforums.org/member.php?u=141830")'s code and it seemed to work, until restart.  Whenever I was running in the terminal, it would sometimes replied with "cannot resolve host <new (then old) hostname>".  I got it sorted out after a screwy app install, so I ended up reinstalling Ubuntu(again). Oh well, thanks anyhow.  It seems as long as I don't try anything...new, Ubuntu is a great OS!  At least I'm not reinstalling thrice weekly as I did with Windoze(POS)! Thanks again!

---

### Post by colau on 2009-08-15
> **theozzlives said:**
> ```
gksu gedit /etc/hosts
gksu gedit /etc/hostname
```
cat /etc/hosts
```

127.0.0.1	ubuntu-desktop	localhost.localdomain	localhost

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
Can I delete these lines below?Are they necessary?
```

::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
And is there any problem if I delete these(bold+red)?
```

127.0.0.1	ubuntu-desktop	**[COLOR="Red"]localhost.localdomain	localhost[/COLOR]**

```

---

### Post by fslezak on 2009-08-15
Now my sudo gives out:

Unable to resolve host cayucos.

It just quits after this :-<

---

### Post by colau on 2009-08-15
> **fslezak said:**
> Now my sudo gives out:

Unable to resolve host cayucos.

It just quits after this :-<
What are you trying to do?

---

### Post by Bachstelze on 2009-08-15
Thread closed due to hijacking.

If you're having issues, start your own.

---


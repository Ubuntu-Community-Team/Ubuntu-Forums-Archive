---
title: "DNS settings messed up and resolvconf unistalled, help me please!"
date: 2016-07-08
forum: Networking &amp; Wireless
---

### Post by mago90 on 2016-07-08
Hi all, my name is Mark, I am new on the forum but not on Ubuntu (been using it since the 12.04). Yesterday I messed up my network settings on lubuntu 16.04. Wifi had problems and I thought it was my problem, it turned out later, that the problem was a temporary problem with the central wifi, it basically showed as connected but I could not load any pages in Firefox. Trying to fix it I am afraid i screwed up my DNS and networking settings
 I followed the advice of doing:
 
 
 sudo apt-get remove --purge resolvconf && sudo apt-get install resolvconf
 
 
 
 
 So I removed resolvconf but then of course I could not re-install it because internet was not working
 
 
 
 
 I can "ping 8.8.8.8" but I can't reach google.com as i get:
 
 
 ping: unknown host google.com
 
 
 This, as far as I understood means a DNS problem.
 I think resolvconf is necessary for fixing my problem , I tried editing the config file adding
 
 
 nameserver 8.8.8.8   nameserver 8.8.8.4
 
 
 But It does not work
 
 
 
 
 On my laptop fortunately I also have Windows 10 on a small partition, I used it to download the .deb file of resolvconf from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but it gives me a MIMEtype error and does not let me install it.
 I tried downloading the tar.gz but when I extract it i cant do
 
 
 ./config   (or ./configure)
 
 
 because i get:
 
 
 debconf: DbDriver  "passwords" warning: could not open /var/cache/debconf/passwords.dat:  Permission denied   Template parse error near `# These templates have  been reviewed by the debian-l10n-english', in stanza #1 of  ./templates
 
 
 How do I reinstall resolvconf and how do I fix the " ping: unknown host google.com" internet problem?
 
 
 I tried to look on the forum and online but no luck so far
 
 
 I am desperate as I am on holiday and I really need Lubuntu connected to the network, Windows 10 is damn slow and I don't like it
 
 
 If anyone can help it would be great!
 
 
 Thank you in advance

---

### Post by praseodym on 2016-07-09
Add the DNS manually:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
```
Restart the network

---

### Post by mago90 on 2016-07-10
Thank you praseodym for your reply!

I tried what you suggested but opening terminal and running that I get:

```
marco@marco-HP-Pavilion-Notebook:~$ echo -e "nameserver 8.8.8.8\ nameserver 8.8.4.4" | sudo
tee /etc/resolv.conf
[sudo] password for marco:
tee: /etc/resolv.conf: No such file or directory
nameserver 8.8.8.8
ameserver 8.8.4.4

```

Any idea??

---

### Post by Bucky Ball on 2016-07-10
Boot into Windows. Check the DNS setting that is using. Boot into Ubuntu. Use the same.

---

### Post by steeldriver on 2016-07-10
Hmm...

```
tee: /etc/resolv.conf: No such file or directory
```

is puzzling - tee should be able to create the file if it's missing altogether - maybe the symlink to run is broken and needs to be removed forcibly? What is the output of

```

ls -ld /etc/resolv*

```

---

### Post by praseodym on 2016-07-10
You had a tippo, it is "\nn". Please run first:
```

sudo touch /etc/resolv.conf
```

---

### Post by mago90 on 2016-07-13
@praseodym I tried to run it again and i get:
```
[sudo] password for marco:
nameserver 8.8.8.8
nameserver 8.8.4.4

```

But I did not know how to restart the network so I restarted the pc but once restarted did not work and the conf file was still empty. How do I restart the network?

@steeldriver 

```
marco@marco-HP-Pavilion-Notebook:~$ ls -ld
drwxr-xr-x 40 marco marco 4096 Jul 12 23:03 .
marco@marco-HP-Pavilion-Notebook:~$ /etc/resolv*

```

@praseodym 

```
marco@marco-HP-Pavilion-Notebook:~$ sudo touch /etc/resolv.conf
[sudo] password for marco:
touch: cannot touch '/etc/resolv.conf': No such file or directory
```

So I tried to get into the directory

```
marco@marco-HP-Pavilion-Notebook:~$ cd /etc
marco@marco-HP-Pavilion-Notebook:/etc$ sudo touch /etc/resolv.conf
touch: cannot touch '/etc/resolv.conf': No such file or directory
marco@marco-HP-Pavilion-Notebook:/etc$
```

Thanks all guys for the help you are providing :)

---

### Post by mago90 on 2016-07-16
I still haven't solved this problem :(

---

### Post by steeldriver on 2016-07-16
```

ls -ld /etc/resolv*

```

all on one line please

---

### Post by mago90 on 2016-07-16
Hi steeldriver I got this:

```
 marco@marco-HP-Pavilion-Notebook:~$ ls -ld /etc/resolv*
 lrwxrwxrwx 1 root root 29 Jun  6 20:19 /etc/resolv.conf -> ../run/resolvconf/resolv.conf
 
```

Don't know if it matters but that output was in light red.

---

### Post by steeldriver on 2016-07-16
Yeah sounds like a broken (dangling) symlink - let's try

```

sudo rm /run/resolvconf/resolv.conf

```

then proceed with 

```

echo '8.8.8.8' | sudo tee /etc/resolv.conf

```

If that works, next step is to try something like

```

ping -c4 google.com

```

If it resolves successfully, at that point you should be able to reinstall the resolvconf package from the respository.

---

### Post by mago90 on 2016-07-26
Still no luck. I don't want to reinstall the whole OS just for this :(

---

### Post by steeldriver on 2016-07-26
I'm happy to continue to help you diagnose the issue, but you'll need to give more feedback than just "still no luck" - what happened exactly when you typed each of the commands? what error messages were produced? what steps did you take afterwards to check the status of your connection (pings? DNS lookups?) and what were the results?

---

### Post by mago90 on 2016-07-26
Apologies steeldriver! I dont know why but i am having trouble using the forum (lots of downtime errors) and I had not seen your reply (had no internet at home hence my reply today) my "still no luck" was not intended to be my answer to your reply (which as I said i had not even seen) but only an attempt to show that I had not solved the issue. Thank you again for your help I will try those commands tomorrow and let you know :)

---

### Post by steeldriver on 2016-07-26
No problem - yes the forum glitches have made things frustrating. Let us know how you get on, I will keep an eye on this thread regardless.

---

### Post by mago90 on 2016-07-27
I tried the commands you suggested and I got:

```
 marco@marco-HP-Pavilion-Notebook:~$ cd /etc
 
 
 marco@marco-HP-Pavilion-Notebook:/etc$ sudo rm /run/resolvconf/resolv.conf
 
 
 [sudo] password for marco:  
 
 
 rm: cannot remove '/run/resolvconf/resolv.conf': No such file or directory
 
```


I checked the /etc folder and the resolv.conf file is not there but I can see a “resolv.conf” symbolic link.

and

```
 marco@marco-HP-Pavilion-Notebook:/etc$ echo '8.8.8.8' | sudo tee /etc/resolv.conf
 tee: /etc/resolv.conf: No such file or directory
 8.8.8.8
 
 
 
```

and 

```
 marco@marco-HP-Pavilion-Notebook:/etc$ ping -c4 google.com
 ping: unknown host google.com
 
```

Greetings

---

### Post by steeldriver on 2016-07-27
Hmm... what does

```

readlink -f /etc/resolv.conf

```
say?

---

### Post by mago90 on 2016-07-28
This is weird but that command seems not to have any effect, I get:

```
 
marco@marco-HP-Pavilion-Notebook:~$ readlink -f /etc/resolv.conf
marco@marco-HP-Pavilion-Notebook:~$
 
```

:o

---

### Post by steeldriver on 2016-07-28
OK let's try a different tack. Please run

```

sudo dpkg-reconfigure resolvconf

```

It should present you with a question about  preparing /etc/resolv.conf for dynamic updates - answer "Yes". It may  also present you with another question about temporarily appending your  existing config to the dynamic one - I suggest answering "No" to that  one.

---

### Post by mago90 on 2016-07-29
I don't get any question, what I get instead is this:
```
 marco@marco-HP-Pavilion-Notebook:~$ sudo dpkg-reconfigure resolvconf
 [sudo] password for marco:  
 dpkg-query: package 'resolvconf' is not installed and no information is available
 Use dpkg --info (= dpkg-deb --info) to examine archive files,
 and dpkg --contents (= dpkg-deb --contents) to list their contents.
 /usr/sbin/dpkg-reconfigure: resolvconf is not installed
 marco@marco-HP-Pavilion-Notebook:~$ 
 
```

I knew that "resolvconf" was not installed but I can't reinstall it as I can't connect to internet!

---

### Post by steeldriver on 2016-07-29
Sorry my memory isn't what it was - I'd forgotten how all this started

Maybe we are overcomplicating things - have you tried simply 

```

sudo rm /etc/resolv.conf

```

yet? If that works, try again with

```

echo '8.8.8.8' | sudo tee /etc/resolv.conf

```

---

### Post by mago90 on 2016-07-29
Don't worry :)

I got :
```

marco@marco-HP-Pavilion-Notebook:~$ cd /etc
marco@marco-HP-Pavilion-Notebook:/etc$ sudo rm /etc/resolv.conf
[sudo] password for marco: 
rm: cannot remove '/etc/resolv.conf': No such file or directory
marco@marco-HP-Pavilion-Notebook:/etc$ echo '8.8.8.8' | sudo tee /etc/resolv.conf
8.8.8.8
marco@marco-HP-Pavilion-Notebook:/etc$  

```

---

### Post by praseodym on 2016-07-29
Syntax is

```
echo 'nameserver 8.8.8.8' | sudo tee /etc/resolv.conf
```

---

### Post by steeldriver on 2016-07-29
OK ... so this time, 'tee' didn't complain? that's a good sign at least

Unfortunately I screwed up the command - it should have been

```

echo '**nameserver** 8.8.8.8 | sudo tee /etc/resolv.conf

```

If there are no errors this time then please follow up with

```

ping google.com

```

and if THAT works, try reinstalling the package

```

sudo apt-get install --reinstall resolvconf

```

---

### Post by mago90 on 2016-07-29
Yes! It worked! I fixed my internet problem! Thank you very much!

Somewhere i had read that sometimes resolv.conf can be overwritten when you restart the computer, so I tried to restart the computer and checked if internet was working and it was!
Lessons learned: if wifi does not work don't assume it is your computer and don't rush to uninstall stuff unless you know what you are doing because it might take weeks to fix it :D

---

### Post by steeldriver on 2016-07-29
That's great

Sorry it took so long to nail it - thanks for you patience

---

### Post by mago90 on 2016-08-01
Don't worry you helped me a lot!I don't see buttons to give you a stars or karma so Again thank you for your help :)

ps: I have no idea how, but should I put "Solved" to the thread??

---


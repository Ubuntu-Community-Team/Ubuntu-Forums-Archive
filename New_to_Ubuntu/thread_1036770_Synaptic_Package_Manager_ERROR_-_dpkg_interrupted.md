---
title: "Synaptic Package Manager ERROR - dpkg interrupted"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by abah01 on 2009-01-11
Anyone out there - looking for help... I have been on a long journey for a nobody in Ubuntu and Linux ---- but thanks to info from the web including these forums I have managed to install Ubuntu + Virtualbox running XP in my Acer Aspire One SSD (truly a lot of bungling around and finally discovering the right path). I still have some issues with sound and also running latest Java version, and in trying to sort this out, suddenly after running Synaptic Package Manager (which never had any problems before) this error message is generated and I cannot proceed anymore---

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Searching thru the web, I have not been able to find anything which can help. So as my 1st official posting in any Ubuntu forum ----- HELP!!!!

---

### Post by abah01 on 2009-01-11
Anyone out there - looking for help... I have been on a long journey for a nobody in Ubuntu and Linux ---- but thanks to info from the web including these forums I have managed to install Ubuntu + Virtualbox running XP in my Acer Aspire One SSD (truly a lot of bungling around and finally discovering the right path). I still have some issues with sound and also running latest Java version, and in trying to sort this out, suddenly after running Synaptic Package Manager (which never had any problems before) this error message is generated and I cannot proceed anymore---

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Searching thru the web, I have not been able to find anything which can help. So as my 1st official posting in any Ubuntu forum ----- HELP!!!!

---

### Post by Oak37 on 2009-01-11
There might be some broken packages, did you run
```
dpkg --configure -a
```

---

### Post by Elfy on 2009-01-11
Run it as root

```
sudo dpkg --configure -a
```

I don't quite know what it was you searched for, but in future search for the actual error message.

In addition to searching the forum, you can also search google and add site:ubuntuforums.org to the search string - will look here.

I use a couple of search engines myself - [www.uboontu.com](www.uboontu.com) and [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

Also can you please not post the same question more than once, while this was a simple enough fix - if it was more complicated then no-one knows what's going on in other threads if it's duplicated.

Lastly I can see that these threads are you're first posts - so welcome to the forum. You might find this helpful

[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)

---

### Post by abah01 on 2009-01-11
Anyone out there - looking for help... I have been on a long journey for a nobody in Ubuntu and Linux ---- but thanks to info from the web including these forums I have managed to install Ubuntu + Virtualbox running XP in my Acer Aspire One SSD (truly a lot of bungling around and finally discovering the right path). I still have some issues with sound and also running latest Java version, and in trying to sort this out, suddenly after running Synaptic Package Manager (which never had any problems before) this error message is generated and I cannot proceed anymore---

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

Searching thru the web, I have not been able to find anything which can help. So as my 1st official posting in any Ubuntu forum ----- HELP!!!!

---

### Post by nothingspecial on 2009-01-11
> **Oak37 said:**
> There might be some broken packages, did you run
```
dpkg --configure -a
```

With sudo in front of it?

---

### Post by Partyboi2 on 2009-01-11
Hi
Open a terminal (Applications>Accessories>Terminal) and type
```
sudo dpkg --configure -a
```

---

### Post by bartolomeo474 on 2009-01-11
ok but on my synaptic all of those comends aren't working sory 4 my english

---

### Post by Elfy on 2009-01-11
> **bartolomeo474 said:**
> ok but on my synaptic all of those comends aren't working sory 4 my english

You have to enter them in a terminal, if it doesn't work there will be an error message, what is it?

Paste it either in a thread of your own or here.

---

### Post by abah01 on 2009-01-11
Thanks a lot - adding 'sudo' works for me!! I tried it prior to posting thread without 'sudo' (didnt work), think I learnt something extra here...
Anyway didnt intend to post 3 threads - the first 2 appeared to be failed attempts what with the error sending messages that i received from the forum -- now I know better (ignore the error message and assume its gone thru)
Thanks everyone!! Now its back to figuring out the audio and java issues....

---

### Post by New Bie on 2009-02-15
Whenever I start Synaptic Package Manager I get the following message

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report

Actually when I was downloading and installing a package my PC got restarted from then on I am geting the above message 

I also tried the above mentioned commands but i am getting the following error

```
root@ubuntu:/home/deathlord# sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 1:
 MSDOS EOF (^Z) in field name `

```

Somebody please help out..!!

---

### Post by kkzman on 2009-03-08
I am having the same problem E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct problem
E:_cache-> open()failed, Please report.

Iran the  dpkg --configure -a and got this message

 root@kevin-desktop:/home/kevin# dpkg --configure -a
Setting up libc6 (2.8~20080505-0ubuntu9) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error
dpkg: subprocess post-installation script returned error exit status 135
root@kevin-desktop:/home/kevin# 


Can anyone please help?

---


---
title: "UltraSurf on Ubuntu?"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by feras.ws on 2008-12-05
Dear Sirs,

how are you ? I had recently moved into Ubuntu completely :) and it's soooooooo nice but I used to use Ultra surf for my proxy to open blocked websites , so is there any program for Linux which do the same ?

Best Regards
Feras

---

### Post by sonicb00m on 2008-12-05
there probably are but in the meantime you can browse blocked sites with

[www.hidemyass.com](www.hidemyass.com)

if that helps you until you get a better solution.

---

### Post by feras.ws on 2008-12-05
:) thank you for ur assistance ! 
but unfortunately it's also blocked .

Regards
Feras

---

### Post by binbash on 2008-12-05
I dont know in which country you live in BUT, editing /etc/hosts and using opendns's dns servers, works for my country's website block

---

### Post by feras.ws on 2008-12-05
Actually i'm from Syria!!

---

### Post by izenteno on 2008-12-05
Try using TOR and privoxy.
Its quite the same as ultrasurf. 

you can download it from [http://www.torproject.org/](http://www.torproject.org/)

here are the instructions Im guessing you have ubuntu 8.10 intrepid.

First: (WE WILL TRY TO EDIT THE SOURCE LIST FROM WHERE YOU GET THE PACKAGES) press alt-f2
Type:  ```
gksu gedit /etc/apt/sources.list
```

It will ask for your password

Copy and paste this address:
```

deb http://mirror.noreply.org/pub/tor intrepid main
deb-src http://mirror.noreply.org/pub/tor intrepid main
```

SAVE THE CHANGES.

NOW OPEN THE TERMINAL (you can find it at accesories)
TYPE THE GPG commands... (THIS IS DONE TO PROVE THAT YOU ARE DL TOR FROM A TRUSTED SERVER, IT ALSO WORKS FOR FURTHER UPDATES/UPGRADES). THIS IS SOMETHING KNOWN AS APT-KEYRING.

```
$ gpg --keyserver subkeys.pgp.net --recv 94C09C7F
$ gpg --fingerprint 94C09C7F
```

YOU SHOULD GET THE NEXT ANSWER AT YOUR TERMINAL:
 
```
pub   1024D/94C09C7F 1999-11-10
         Key fingerprint = 5B00 C96D 5D54 AEE1 206B  AF84 DE7A AF6E 94C0 9C7F
   uid       [ultimate] Peter Palfrader
```

AFTER PROVING THE FINGER PRINT YOU SHOULD ADD THIS KEY, YOU CAN ACHIVE THIS BY:

```
$ gpg --export 94C09C7F | sudo apt-key add -

```

NEXT STEP:
AT THE TERMINAL TYPE THIS COMMAND

```
sudo apt-get update
sudo apt-get install tor
```


I hope this help you. You should continue the tutorial to set the privoxy and for DL the add-on for firefox (tor buttom). Read the web page of tor tells you how to remain anonimous.

[http://www.torproject.org/]("http://www.torproject.org/")

---

### Post by feras.ws on 2008-12-08
thank you for your assistance I really appreciate that.
but just one question , can I disable it easily ?

Regards
Feras

---

### Post by 3rdalbum on 2008-12-08
> **feras.ws said:**
> thank you for your assistance I really appreciate that.
but just one question , can I disable it easily ?


The link that the previous poster gave has instructions about installing the "Tor button" for Firefox. With the Tor Button, you can switch from proxy to normal connection with just a little button in the bottom-right corner of your Firefox window.

So, to answer your question, yes, it's very easily disabled.

---

### Post by izenteno on 2008-12-10
> **feras.ws said:**
> thank you for your assistance I really appreciate that.
but just one question , can I disable it easily ?

Regards
Feras

 Im glad this helped you! 
Is it working good enough. For mantaining privacy you also need an add-on named cookie culler. Help you clean cookies. Also you should use something to block scripts.

---

### Post by feras.ws on 2008-12-10
yes it's working with no problems ;)
i'll check this add-on

Regards
Feras

---

### Post by izenteno on 2008-12-11
By the way, If sometimes you dont find exactly what you are looking for you in a linux version you can always try "WINE" windows emulator, I havent use it myself but I heard you can even use ultrasurf there...

---

### Post by feras.ws on 2008-12-12
thank you (F)
I also heard about wine but do you know what?
I hate Microsoft :S or anything can make me remember that trash !!

Best Regards
Feras

---

### Post by loneowais on 2009-03-31
I couldn't solve the problem

I'm behind my School proxy

it is: 172.16.200.1:3128

My friends use Ultra Surf on Windows and it works just fine..

But I can't do it even with TOR/Privoxy.

Please write a step by step guide someone..

---

### Post by habibvalil on 2009-08-18
when I use this command as mentioned in previous posts:  gpg --keyserver subkeys.pgp.net --recv 94C09C7F    I get a failed response:   gpg: requesting key 94C09C7F from hkp server subkeys.pgp.net  gpg: keyserver timed out  gpg: keyserver receive failed: keyserver error   any solutions?

---

### Post by barry.yarl on 2009-09-07
same as habibvalil here need help plz

---

### Post by cariboo on 2009-09-07
We do not support the circumvention of rules. this thread is closed.

@loneowais your school has rules set in place for a reason, we will not help you get around them.

---


---
title: "gpg: keyserver timed out"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by Suan_gr on 2011-08-02
I am just a beginner. I am unable to install software from package manager due to GPG- no pub-key.

The following command doesn't work: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 35DA01C261E46227

because I keep getting this error message.

gpg: requesting key 61E46227 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Please help! :confused:

---

### Post by bodhi.zazen on 2011-08-02
That happens from time to time. The other possibility is you running a firewall ?

Either try again or try a different key server (they all mirror each other).

google search for a key server near you ;)

---

### Post by Suan_gr on 2011-08-02
Thank you for the reply but isn't really helping. Could you be a little more specific? Like I mentioned, I'm a beginner and don't know much. ty!

---

### Post by bodhi.zazen on 2011-08-02
with your browser, go to google.com

enter "gpg key servers" with out quotes in the search box

Look through the results for alternate gpg servers

Choose any one you wish, any one should work, put the alternate gpg server in your command

```
sudo apt-key adv --keyserver keyserver.your.found.from.google --recv-keys 35DA01C261E46227
```

substitute "keyserver.your.found.from.google" with any of the alternate key servers listed from your google search.

---

### Post by Suan_gr on 2011-08-02
Done! tysm :D

---

### Post by bodhi.zazen on 2011-08-02
> **Suan_gr said:**
> Done! tysm :D

Fantastic , glad you got it solved.

---

### Post by cbennett926 on 2011-08-02
Ok, this isn't really a solution type comment, but what exactly is a key server?

---

### Post by bodhi.zazen on 2011-08-02
> **cbennett926 said:**
> Ok, this isn't really a solution type comment, but what exactly is a key server?

A gpg server is a place where one stores public gpg keys.

See: [http://www.madboa.com/geek/gpg-quickstart/](http://www.madboa.com/geek/gpg-quickstart/)

So if you wish to gpg sign a document, or package, you can upload your public gpg key for others to download.

For the most part all the key servers sync with eachother, so if you upload your kek to server A it will be available on servers A,B,C ...

You get the idea.

---

### Post by cbennett926 on 2011-08-02
Oh ok! Thank you so much! I really wanna learn as much about Linux as possible but it's very difficult to find the most up to date book :/

---

### Post by bodhi.zazen on 2011-08-02
> **cbennett926 said:**
> Oh ok! Thank you so much! I really wanna learn as much about Linux as possible but it's very difficult to find the most up to date book :/

Just keep using Linux and asking questions. Most of us learn as we go.

---


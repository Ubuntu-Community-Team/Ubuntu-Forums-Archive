---
title: "Internet Speed"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by Yazan on 2010-07-14
Hello everyone, I would like help with the Internet speed ;S
I have couple of questions and I hope it's going to be easy for you to answer. 
Question 1: I would like to know what's the difference between downloading a program or a piece of software through the terminal and downloading it via the web browser.

Question2: I would really appreciate it if someone would help me and check the Skype downloading page. I'm trying to download Skype, I've tried through the terminal and through the web browser and the downloading percentage keeps on stopping at 14% for some odd reason.

Question 3: Why when downloading through the terminal it sucks the whole internet speed and takes it in download. The pages dies before it's loaded and takes maybe an hour to view it's content. However when download is over, it goes back quick. Thanks.

---

### Post by ubunterooster on 2010-07-14
1: It is slightly faster to download via CLI (command Line Interface)

2: it's flying here (also; is it available through the "Software Center" because it is in Mint's)

3 The CLI takes full priority of your Internet in my experience

---

### Post by Yazan on 2010-07-14
> **ubunterooster said:**
> 1: It is slightly faster to download via CLI (command Line Interface)

2: it's flying here (also; is it available through the "Software Center" because it is in Mint's)

3 The CLI takes full priority of your Internet in my experience
Thanks for the quick answers. 
Alright, by the Software Center you mean Synaptic Package Manager?

---

### Post by ubunterooster on 2010-07-14
No, the "Ubuntu Software Center"

---

### Post by Yazan on 2010-07-14
Thanks again. However now I'm facing another problem. The problem is that when I was installing it for the first time, and it stopped at that certain percentage, I closed the terminal through the X button. And now, it's giving me an error about it. I would like to know how to solve it.
[B]
Previous installation hasn't been completed[/B]
The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software.

---

### Post by ubunterooster on 2010-07-14
I had this error seen before here:


[QUOTE=zvacet;9157847]In applications>accessories>terminal type

```
sudo dpkg --configure -a
```and 

```
sudo apt-get -f install
```If you get any errors from these  commands,please post them here.

---

### Post by Yazan on 2010-07-14
> **ubunterooster said:**
> I had this error seen before here:


[QUOTE=zvacet;9157847]In applications>accessories>terminal type

```
sudo dpkg --configure -a
```and 

```
sudo apt-get -f install
```If you get any errors from these  commands,please post them here.
Thanks really really much man. And I just used the first command and it worked fine.

---

### Post by ubunterooster on 2010-07-14
Excellent! Glad to have helped. :D

---

### Post by libssd on 2010-07-14
Re #2: Having spent literally days trying to get Skype to work with Isadora/Lucid, I have concluded that it is a complete waste of time until the Skype people get their act together and release a better version for Linux. I've corresponded with Skype tech. support, looked for answers in various places, all to no avail. The best I could get was very sketchy sound from microphone input -- completely useless.

Many others share my lack of enthusiasm for the latest version of Skype. Save your energy for exploring software that actually works.

---

### Post by ubunterooster on 2010-07-14
> **libssd said:**
> Re #2: Having spent literally days trying to get Skype to work with Isadora/Lucid, I have concluded that it is a complete waste of time until the Skype people get their act together and release a better version for Linux. I've corresponded with Skype tech. support, looked for answers in various places, all to no avail. The best I could get was very sketchy sound from microphone input -- completely useless.

Many others share my lack of enthusiasm for the latest version of Skype. Save your energy for exploring software that actually works.
I got mine form the Mint Software center and have no problem (in test call)

---

### Post by oldsoundguy on 2010-07-14
> **libssd said:**
> Re #2: Having spent literally days trying to get Skype to work with Isadora/Lucid, I have concluded that it is a complete waste of time until the Skype people get their act together and release a better version for Linux. I've corresponded with Skype tech. support, looked for answers in various places, all to no avail. The best I could get was very sketchy sound from microphone input -- completely useless.

Many others share my lack of enthusiasm for the latest version of Skype. Save your energy for exploring software that actually works.

Skype in Lucid (at least on my desktop) does not work AT ALL .. my Logitech 9000 works fine in Cheese and the audio checks out.

Launch Skype and nothing happens (using the beta piece of crap!) other than the fact that I have to kill the process as it won't close/exit under normal controls.

---

### Post by ubunterooster on 2010-07-14
Sorry it does not work for you guys, but please do not hijack other's threads insisting that they should not be using a program

---


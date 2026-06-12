---
title: "A new beginer trying to learn to solve failure notices"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Anne Sejer on 2009-01-17
OK guys, a new beginner here, I have installed Ubuntu on to my 6 year old Dell Inspiron 8600, and despite the confusion of learning a new operating systems GUI, I like it. Even better it seems to work! That is until I recieved the following message while trying to add Scribus.

-----------------------------------------------------------
Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
--------------------------------------------------------------



My first reaction was to go to the Synaptic program under administration and then I recieved another error preventing that from starting:

-------------------------------------------
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
----------------------------------------------


I have no idea of how to "manually run" anything...... What now.

Many thanks in advance to all helpfull soles.

Kindly,
Anne Sejer, Denmark

---

### Post by mikewhatever on 2009-01-17
Go to Applications->Accessories->Terminal, enter <sudo dpkg --configure -a> without brackets, hit Enter, then your password.

---

### Post by Anne Sejer on 2009-01-17
Hi Mike, and thanks for the help, as well as the link.... social commentary aside, there is one point missing - we are all people together on this spinning rock, and computers are very much a social tool - success can therefore be partially measured by accessability for the uninitiated. Having said this we uninitiated can measure our success by how quickly we learn to initiate ourselves to a level where we can actually contribute to the socializing process.... hmm maybe a bit too much filosofi for a staturday afternoon. 

Now down to the nitty grity. You're solution worked for getting the synaptic program to run again, but the new program installation program still complains uninteligably (for someone that doesn't know alot about that sort of stuff). I'll keep playing with it.... Until further notice thanks for the input!

---

### Post by nothingspecial on 2009-01-17
What does it say?

---

### Post by ibizatunes on 2009-01-17
Welcome these are a few useful thing and ideas that you may need help with

if you want to play restricted formats ie dvd's you need medibuntu
[www.medibuntu.org](www.medibuntu.org)

if you go to the terminal
(application > accessories > terminal) 

and paste this 

```
sudo apt-get install ubuntu-restricted-extras
```

This will install adobe flash, and java and few other bit of software


if you go to system > admin > synaptic package management

Here you can install thing like VLC (a open source mediaplayer)
There are thousand of application to pick from within the package management

Every struggles with ubuntu when they first load it, but it is well worth it

Post up your error and problem as someone will try to fix it

---

### Post by glotz on 2009-01-17
[QUOTE=ibizatunes]Welcome these are a few useful thing and ideas that you may need help with

if you want to play restricted formats ie dvd's you need medibuntu
[www.medibuntu.org](www.medibuntu.org)

if you go to the terminal
(application > accessories > terminal) 

and paste this 

```
sudo apt-get install ubuntu-restricted-extras
```

This will install adobe flash, and java and few other bit of software


if you go to system > admin > synaptic package management

Here you can install thing like VLC (a open source mediaplayer)
There are thousand of application to pick from within the package management

Every struggles with ubuntu when they first load it, but it is well worth it

Post up your error and problem as someone will try to fix it[/QUOTE]

I suggest you ignore this completely unrelated (bad in my opinion) advice.

---

### Post by albinootje on 2009-01-17
> **Anne Sejer said:**
>  Now down to the nitty grity. You're solution worked for getting the synaptic program to run again, but the new program installation program still complains uninteligably (for someone that doesn't know alot about that sort of stuff).

If you post the error message or a screenshot of it, then we can help you with that.

Meanwhile, check out these :
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

### Post by Anne Sejer on 2009-01-17
Bingo! Thank you all for your response!! Itis not the price but the spirit which has brought me to Ubuntu, and I must say my first query to the community has reaffirmed my belief in the open source process/ community. Thanks! I hope to be able to supprt others in the same manner you have supported me one day.

Anne, DK

---

### Post by mikewhatever on 2009-01-17
> **glotz said:**
> i suggest you ignore this completely unrelated (bad in my opinion) advice.

+1.

> **Anne Sejer said:**
> Bingo! Thank you all for your response!! Itis not the price but the spirit which has brought me to Ubuntu, and I must say my first query to the community has reaffirmed my belief in the open source process/ community. Thanks! I hope to be able to supprt others in the same manner you have supported me one day.

Anne, DK

Is the problem solved then? You might want to update the thread for whoever might read it in the future.

---

### Post by albinootje on 2009-01-17
> **mikewhatever said:**
> +1.


I didn't see anything bad in that comment.
It looked to me like handing out some useful first steps for a new Ubuntu user.
Don't understand why several people have something against this.

---

### Post by mikewhatever on 2009-01-17
Bad may be a bit strong, but first, those suggestions were not at all related to the help request by the OP, second, installing restricted extras or any other package wouldn't work, given there is a problem with apt. Now, do you really think it very helpful to suggest installing vlc,java and codecs, when the user wants Scribus and to fix apt error?

---

### Post by albinootje on 2009-01-17
> **mikewhatever said:**
>  installing restricted extras or any other package wouldn't work, given there is a problem with apt.

My bad :( you're right.

---


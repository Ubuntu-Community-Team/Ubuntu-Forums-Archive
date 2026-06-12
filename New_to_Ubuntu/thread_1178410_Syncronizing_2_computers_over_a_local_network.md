---
title: "Syncronizing 2 computers over a local network"
date: 2009-06-04
forum: New to Ubuntu
---

### Post by Sayadina on 2009-06-04
Hy... 


I have a little issue... I have 2 computers at home, both run Ubuntu operating system. Now, i have some folders on them, that i need to contain the same files. Cause i go out with my leptop, and work on it while i'm at university, and need to continue this at home, and it is getting a litle bit too anoying to replace everything thru share folders. Not to say that i sometimes forget to do the updates, and modify other files, and then i have to compare them to see who goes where in the replacing... 


I know that on windows systems i can syncronize folders (never tried on different computers over the same network, but should work also)

So... my question is: how can i syncronize the folder "x-zone" from my Big computer to my Leptop, and vice versa, via the network?

I have tried to play with Grsync and rsync and Unison, but I must be doing something worng, cause i can't manage to do the syncronization over the network.


Thank you in advance

---

### Post by decoherence on 2009-06-04
rsync or unison are the right tools. Do they give you any information about why they're failing?

Can you give us the command you used for rsync? Here is an example that should work.

```
rsync -avz ~/myDirectory decoherence@10.9.1.10:~/myDirectory
```

---

### Post by Sayadina on 2009-06-04
This is what i tried and didn't work

```
tanita@Calcu-Mare-Alexa:~$ rsync -avz ~/x-zone tanita@Alexa-amant:~/x-zone
ssh: Alexa-amant: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [sender=2.6.9]
```

or:


```
tanita@Calcu-Mare-Alexa:~$ rsync -avz ~/x-zone tanita@***.***.**.**:~/x-zone
ssh: connect to host ***.***.**.** port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(454) [sender=2.6.9]
```

---


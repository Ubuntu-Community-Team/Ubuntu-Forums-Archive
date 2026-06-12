---
title: "Memory Leak in Ubuntu 10.10 (Maverick)?"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by vasiauvi on 2011-03-24
Good day everyone,
For some time - I don't know from when exactly - my system is very slow, my Ubuntu 10.10 system is remaining without memory very very often.
I have a Asus X51R Laptop with 1GB of RAM and a Dual Core CPU.

Whenever I use Firefox or Google Chrome my Swap is getting full and also my memory is full. I tried to identify where is the problem but I don't get it!

I want to post some print screen of Htop with the memory, processes and swap, if you don't mind:
- first **Firefox 4** running: [http://dl.dropbox.com/u/1518616/Pictures/firefox1.png](http://dl.dropbox.com/u/1518616/Pictures/firefox1.png)
- today just after coming from work started the PC and opened **Google Chrome**: [http://dl.dropbox.com/u/1518616/Pictures/chrome1.png](http://dl.dropbox.com/u/1518616/Pictures/chrome1.png)

I have to point the fact that my swap is limited to 40%, meaning that only 400MB should be swapped! If I put, for example, 80% all will be filled!

I didn't had a lot of tabs opened, maximum 5 on Firefox and only 3 in Chrome. I have addons on both browsers but hoe much RAM I need to run a damn browser???

Can anyone help me some how, just to redirect me somewhere?

Thank you!

---

### Post by stoneage on 2011-03-24
From the screenshots you posted, the browsers are indeed the problem.

Firefox 4 and Chrome open a new process for every tab, that is why they are using so much RAM.

2 tabs = 2 instances of Firefox running, hence RAM x 2.

What I don't know is why they are all still running if you only have 5 plus 3 tabs. Though 8 browsers running simultaneously is still a lot of RAM if you only have 1 GB installed.

---

### Post by vasiauvi on 2011-05-07
Thanks for the reply!

I still didn't find from where is the problem and updated to 11.04 but the memory leakage is high. I really don't understand why 1GB of RAM is not enough for Ubuntu but 512 MB RAM for Windows XP is OK.
Now in 11.04 for example I had opened only Terminal, Opera and Libre Office Writter. Some hours I had to write something and didn't opened other programs but the memory was filled out,and also swap and the load of the system was very high. I don't understand why the SWAP is filling so much and why after closing a tab from browser the memory is not free. 
Also if I let the PC running without using it the LOAD is high after some time...

The system was extremelly slow and closed Opera and Office but Compiz now was tacking a lot of memory.

[IMG]http://http://i.imgur.com/cyJvU.png[/IMG] 
[http://i.imgur.com/cyJvU.png](http://i.imgur.com/cyJvU.png)

After restart, reloading Compiz the Unity is killed...No panels!

Nice! I'm starting to like more and more Ubuntu....

---


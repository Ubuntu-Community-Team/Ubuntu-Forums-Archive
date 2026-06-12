---
title: "Synaptic Package Manager .. HUGH PROBLEM!!!"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by thelonelywind on 2010-05-19
Hello, Well My Problem Started.. While About 3gb's Worth Of Programs  From S.P.M Were Installing I Ran Out Of Hard Drive Space To Install Then  So It Stopped Installing, Gave Me An Error And Closed. I Have Freed Up  The Space Needed But When I Go Back TO S.P.M Theres No Option TO Resume  Install. My Bandwidth Is Very Low And It Will Take Forever To  Re-download All The Programs Again So I Wanted To Know, How Can You Tell  If A Program In The  Synaptic Package Manager Has Already Been  Downloaded. 

Im Just Basically Trying To Install These Programs. I Know The Files Are  Still In My P.C But How Do I Restart That Failed Instillation?? 

Thanx!

---

### Post by thelonelywind on 2010-05-19
Hello, Well My Problem Started.. While About 3gb's Worth Of Programs From S.P.M Were Installing I Ran Out Of Hard Drive Space To Install Then So It Stopped Installing, Gave Me An Error And Closed. I Have Freed Up The Space Needed But When I Go Back TO S.P.M Theres No Option TO Resume Install. My Bandwidth Is Very Low And It Will Take Forever To Re-download All The Programs Again So I Wanted To Know, How Can You Tell If A Program In The  Synaptic Package Manager Has Already Been Downloaded. 

Im Just Basically Trying To Install These Programs. I Know The Files Are Still In My P.C But How Do I Restart That Failed Instillation?? :confused:

Thanx!:KS

---

### Post by thelonelywind on 2010-05-19
[SIZE=2]**Synaptic Package Manager ..Downloaded Or Not Downloaded??!**[/SIZE] 			
 			 			 		   		 		 		[SIZE=2]Hello, Well My  Problem Started.. While About 3gb's Worth Of Programs From S.P.M Were  Installing I Ran Out Of Hard Drive Space To Install Then So It Stopped  Installing, Gave Me An Error And Closed. I Have Freed Up The Space  Needed But When I Go Back TO S.P.M Theres No Option TO Resume Install.  My Bandwidth Is Very Low And It Will Take Forever To Re-download All The  Programs Again So I Wanted To Know, How Can You Tell If A Program In  The  Synaptic Package Manager Has Already Been Downloaded. 

Im Just Basically Trying To Install These Programs. I Know The Files Are  Still In My P.C But How Do I Restart That Failed Instillation?? [/SIZE] [SIZE=2]:confused:

Thanx! [/SIZE][SIZE=2]:KS[/SIZE]

---

### Post by Tholley on 2010-05-19
if you go into Synaptic, on the left somewhere, there will be drop down menu and you should be able to click on "installed packages".
 
Sorry, I'm not on my Ubuntu machine, so doing it by foggy memory.
 
It's there somewhere!

---

### Post by oldos2er on 2010-05-19
Downloaded packages are kept in /var/cache/apt/archives, assuming you haven't changed Synaptic's default behavior. If I'm not mistaken, Synaptic will first check the cache for a package.

---

### Post by cariboo on 2010-05-19
Please don't create multiple threads on the same subject, I have merged your three threads

---

### Post by gdonwallace on 2010-05-20
That is one of the joys of synaptic.  It will download everything and then install everything.  So if you run through the process again, whatever was download prior will not (or should not) be downloaded a second time since it is already on your system.

Just run the process as normal, when its all said and done, everything will get installed.

P.S. I had a similar problem, but had to reboot because my system locked up on me.  I re-ran synaptic; it still showed the same amount of programs / files to update, but when I clicked apply, it picked up where it had left off.

---


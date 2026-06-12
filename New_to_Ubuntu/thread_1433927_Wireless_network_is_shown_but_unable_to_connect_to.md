---
title: "Wireless network is shown but unable to connect to the network"
date: 2010-03-19
forum: New to Ubuntu
---

### Post by ankur1990 on 2010-03-19
Hey fellas
I m using ubuntu 9.10....... my network-manager is showing the wireless networks but it fails to establish the connection when i click on a particular network........ i m getting this problem since i changed the permissions of /etc/ and /var to chmod 777.
is this problem has a relation with the permission or the reason is something else???????
it works fine before some time but not giving this problem.......
i m able to connect to the internet through wired cable dsl but unable to connect through wireless network.........
please help me out fellas....
thanx in advance :)

---

### Post by ayenack on 2010-03-19
What user did you chmod 777 (7 read, 7 write, 7 execute) to and why? If it's not root then root will not be able to connect during boot. You've made a big mess doing this.

There's a whole load of permissions in there so you've got a whole lot of work trying to sort this one out.

Nice tag line though. Iron Maiden do rule!

---

### Post by ankur1990 on 2010-03-20
hey will it get alright if again i restore the permission to default.........
can anybody tell me whats the default permissions of /etc/ and /var so that i can change the permisiions again using the chmod...........
please help me out

---

### Post by ray ray on 2010-03-20
The same thing is happening to me except for that chmod 777 bit. Wireless was working fine earlier but 4 hours ago cut out. My ethernet cable works fine. 

I tried reinstalling the driver but it tells me it's active and in use.

Any ideas or suggestions? I'm very new to Ubuntu--installed 9.10 yesterday on a Dell Vostro 1500 and I got rid of Windows 7 in the process, if any of that matters....

Thanks so much!

---

### Post by ankur1990 on 2010-03-20
@ ray.....
try installing the braodcom driver.....
before the ubuntu patch for the wireless i used that to connect to the wireless.........

---

### Post by ankur1990 on 2010-03-20
> **ayenack said:**
> What user did you chmod 777 (7 read, 7 write, 7 execute) to and why? If it's not root then root will not be able to connect during boot. You've made a big mess doing this.

There's a whole load of permissions in there so you've got a whole lot of work trying to sort this one out.

Nice tag line though. Iron Maiden do rule!

hey yaar i m able to connect by setting the permission to chmod 755.......
thanx for your help anyway ;). I realize my mistake of giving all permissions to other but later i changed it.... reboot and it got connected..
Thanx buddies

---

### Post by ray ray on 2010-03-20
> **ankur1990 said:**
> @ ray.....
try installing the braodcom driver.....
before the ubuntu patch for the wireless i used that to connect to the wireless.........
I have. When I open Hardware Drivers it shows two Broadcom drivers: B43 wireless driver and STA wireless driver.

I have B43 active and in use but still no joy. I feel like when I first set-up the wireless the other driver was in use and when I activated it there was a prompt to reboot and then it worked but now I can't get that one to be the active driver in use....

---

### Post by ankur1990 on 2010-03-22
> **ray ray said:**
> I have. When I open Hardware Drivers it shows two Broadcom drivers: B43 wireless driver and STA wireless driver.

I have B43 active and in use but still no joy. I feel like when I first set-up the wireless the other driver was in use and when I activated it there was a prompt to reboot and then it worked but now I can't get that one to be the active driver in use....

are you able to see the wireless networks available??????
or the problem is that it is showing the networks but unable to connect it?
please give me a detail abt it.........
i will try my level best

---

### Post by ray ray on 2010-03-22
No, I can't see any wireless networks at all. I can add my wireless network but it doesn't pick it or any others up. Ethernet is OK but if I'm not plugged in, it says no networks available. I think it might be the driver because it used to work and the one I had active still shows up in Hardware Drivers but I can't activate it (Broadcom STA wireless driver for a BCM4401).
 
I've tried re-installing it but that doesn't seem to work. Is there something I need to do to uninstall and re-install other than download from Broadcom.com and follow the install directions?
 
Thanks so much!

---

### Post by ankur1990 on 2010-03-22
> **ray ray said:**
> No, I can't see any wireless networks at all. I can add my wireless network but it doesn't pick it or any others up. Ethernet is OK but if I'm not plugged in, it says no networks available. I think it might be the driver because it used to work and the one I had active still shows up in Hardware Drivers but I can't activate it (Broadcom STA wireless driver for a BCM4401).
 
I've tried re-installing it but that doesn't seem to work. Is there something I need to do to uninstall and re-install other than download from Broadcom.com and follow the install directions?
 
Thanks so much!
yeah u can try that one......... intially before ubuntu patch i worked on wireless through it only........ download the driver from [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) along with the readme file and follow the instructions.......
it worked for me in difficult times.... hope it will work for u too :p

---

### Post by gadolinio on 2010-03-22
> **ayenack said:**
> What user did you chmod 777 (7 read, 7 write, 7 execute) to and why? If it's not root then root will not be able to connect during boot. 

You don't chmod 777 a user, but a folder or file.
Each 7 has the three permissions itself, as it's the sum of 4 (read) + 2 (write) + 1 (execute).
First 7 means read&write&execute permission for the user from whose terminal the command was written.  The second one means read&write&execute permission for the user's group. The last one sets read&write&execute permission for everybody else.

Regarding the other wireless issue, i had those symptoms but after buying the computer (i mean wireless had never worked before) and could solve the problem with a kernel upgrade, and then a specific driver install... Hope you find this somewhat useful...

---

### Post by ayenack on 2010-03-22
> **gadolinio said:**
> You don't chmod 777 a user, but a folder or file.
Each 7 has the three permissions itself, as it's the sum of 4 (read) + 2 (write) + 1 (execute).
First 7 means read&write&execute permission for the user from whose terminal the command was written.  The second one means read&write&execute permission for the user's group. The last one sets read&write&execute permission for everybody else.

Regarding the other wireless issue, i had those symptoms but after buying the computer (i mean wireless had never worked before) and could solve the problem with a kernel upgrade, and then a specific driver install... Hope you find this somewhat useful...

I didn't say you did, read the post again. What you can do is give permissions on a folder/s to an individual user simple as that. And I know fully what the 777 means without a lesson from you.

---

### Post by ankur1990 on 2010-03-23
> **ayenack said:**
> I didn't say you did, read the post again. What you can do is give permissions on a folder/s to an individual user simple as that. And I know fully what the 777 means without a lesson from you.
chill buddy ;)...i came to know abt my mistake and then corrected it by setting 755 permission and all is well now...
so take a chill :p

---

### Post by ray ray on 2010-03-23
I'll give it a shot tonight. Thanks! =)

---

### Post by gadolinio on 2010-03-23
> **ayenack said:**
> I didn't say you did, read the post again. What you can do is give permissions on a folder/s to an individual user simple as that. And I know fully what the 777 means without a lesson from you.

Hey i had no intention to attack you; i'm sorry if i gave you that impression.
I was just trying to contribute with what i know. You may know exactly whay 777 means, but other people may not. I'm not giving you a lesson; i'm making a comment.
And if you give some file the 777 permissons, the user doesn't matter because everyone has all the permissons. (indeed, i don't know if it ever matters, if the file's owner is still the same, the group is still the same, and everybody else is everybody else).
Again, i apologize if my post sounded rude or unrespectful to you.

---

### Post by ayenack on 2010-03-24
OK everyone. I get the point.

I responded in a way that's un-common for me and after re-reading my post I can see that I was not clear enough on my definition of 777.

If anyone needs to know anything about changing permissions then visit:-

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

@gadolinio.

You're right that the user does not matter but root does need ownership over some folders and scripts etc....

I was rude to you and for that apologies.

---

### Post by ankur1990 on 2010-03-24
> **ayenack said:**
> OK everyone. I get the point.

I responded in a way that's un-common for me and after re-reading my post I can see that I was not clear enough on my definition of 777.

If anyone needs to know anything about changing permissions then visit:-

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

@gadolinio.

You're right that the user does not matter but root does need ownership over some folders and scripts etc....

I was rude to you and for that apologies.
ubuntu creates brotherhood too ;)
ubuntu rocks :D

---

### Post by ankur1990 on 2010-03-24
> **ray ray said:**
> I'll give it a shot tonight. Thanks! =)
whats the result of your try?
is it wrking?

---

### Post by gadolinio on 2010-03-24
Haha Ubuntu does rock, indeed!

@ayenack
__No problem. Just writing does not always let us be as clear as we'd like to be, and misunderstandings take place.
I'm glad this is settled now!

And ankur1990 solved his problem... Ahhh we should all go and listen to Iron Maiden now! haha... :guitar:

---

### Post by ankur1990 on 2010-03-24
> **gadolinio said:**
> Haha Ubuntu does rock, indeed!

@ayenack
No problem. Just writing does not always let us be as clear as we'd like to be, and misunderstandings take place.
I'm glad this is settled now!

And ankur1990 solved his problem... Ahhh we should all go and listen to Iron Maiden now! haha... :guitar:
yeah \m/
listen nd bang ur head :p :p :p

---


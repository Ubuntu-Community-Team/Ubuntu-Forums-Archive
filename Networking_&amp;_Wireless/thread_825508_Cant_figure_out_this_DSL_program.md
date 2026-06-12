---
title: "Cant figure out this DSL program"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by stvdel on 2008-06-11
Hello, I am using DSL and I have tried to connect using
the Ubuntu PPPoe default connection but I have had no 
luck. The reason I have tried this is because I have no 
idea how to install the DSL program the ISP has provided
me to use to connect. Here is the read me from the program
they have given me. If anyone knows anyway they can walk
me through how to install this please help. I am trying
to use 8.04

Here is the read me:

1. It is necessary to have root privileges in order to use this client to access the network.Before getting start, confirm the dhcp client module(dhcpcd) have been installed on your Linux OS and the network interface have been set up to "Use dynamic Ip configuration ". The version of c share lib in system is more than 2.3.



2. Install: Extract the installing file to the path(denoted by $dest_path. $dest_path should be used below, and should be changed to actual value when you use it), and then it is ok.



3. Environment setting: environment variable RACERC=$dest_path should be added to root user, and $dest_path should be added to PATH environment variable of root user.



4. Configuration: Edit the file racer.ini to modify the value of Server1 and Server2. Server1 and Server2 mean the ip address of server. Server1 and Server2 should be set to one server ip if there is only one server ip address.



5. User's guide:


Logon: $dest_path/racer/ecou.sh start

Check status: $dest_path/racer/ecou.sh status

logoff: $dest_path/racer/ecou.sh stop

---

### Post by nixscripter on 2008-06-11
Based on how I read it, I would recommend these install instructions:

1. Get root priviledges. That's done with ```
sudo -s
```. You now have a root shell.

2. I don't know what "extract the installing file" means exactly. Is it an archive, like a zip or a tar.gz ? In any case, this step means extract it "somewhere useful." For Ubuntu, I would simply suggest in /usr/local. So, $dest_path = /usr/local, and you can change directory in the shell to /usr/local before you extract.

3. This is an enviornment variable change so the software knows what to do.
```

dest_path=/usr/local
export RACERC=$dest_path

```

Apparently, they want this done whenever you attempt to use the utilities. To make life easier, I changed step 5 with this in mind.

4. Edit the file like they said.

5. To run it, I would suggest a simple shell script, just to avoid the headache.

```

#!/bin/sh
dest_path=/usr/local
export RACERC=$dest_path
/usr/local/racer/ecou.sh $1

```

I would suggest saving that in /usr/local/sbin. Suppose you call the script **runracer.sh** for example.

Now that it's installed, you can go to a shell and type: ```
sudo runracer.sh start
``` to start it. Their step 5 are the three commands you can give it.

Sorry if it's a little complicated. I hope it helps.

---

### Post by stvdel on 2008-06-15
A couple more questions.

So I am guessing you are saying I can skip step 3? 

About step 4, is this asking me to change the ip address to my ip address or some other one?

So step 5 you are saying open gedit paste that script and save the file as runracer.sh under the /usr/local/sbin?

If I am wrong please correct me.

---

### Post by stvdel on 2008-06-15
bump

---

### Post by stvdel on 2008-06-16
bump

---

### Post by nixscripter on 2008-06-16
> **stvdel said:**
> 
So I am guessing you are saying I can skip step 3? 


Yes, I think step 5's workaround will do that for you.

> 
About step 4, is this asking me to change the ip address to my ip address or some other one?


I think it's the PPP server you are connecting to. I'm not sure what that is. Were you told any "server" addresses when you got the instructions?

> 
So step 5 you are saying open gedit paste that script and save the file as runracer.sh under the /usr/local/sbin?


Something like that. You might also want to do: ```
bash -n **script**
``` to check for (my) simple mistakes before you do so.

---

### Post by stvdel on 2008-06-17
When I opened the racer.ini file all it said was server one and had and ip address and then said server 2 and had another ip address listed. If I have to call the isp to ask them about the server ip address I will. 

About your script, I tried to run the script but it says command not found.

I also don't know how to run bash -n script. Where it says script should I be using runracer.sh so it would be bash -n runracer.sh? Also before I run this should I be in a certain directory. I have tried to run it so far but no luck.

---

### Post by stvdel on 2008-06-18
I have attached the racer file to this post, perhaps someone can take a look and give me some advice on what to do.
Thanks

---

### Post by stvdel on 2008-06-19
bump again

---

### Post by nixscripter on 2008-06-19
What command isn't found?

Test the script with "bash -n runscript.sh" if that's what you called it.

If you haven't already, make it executable. Try "chmod +x runscript.sh" in the directory where the script is. If it's in /usr/local as I suggested, then this will let you just type "/usr/local/runscript.sh" at the command line in the future.

---

### Post by stvdel on 2008-06-19
Okay we are getting somewhere, I put in the commands you listed and they seemed to work. So then I tried to start the program but got this.

lai@lai-laptop:~$ cd /usr/local/sbin
lai@lai-laptop:/usr/local/sbin$ sudo runracer.sh start
All names of your net interface installed
-----------------------------------------
eth1 0
Input one name to have access with Internet (eth0): eth1
The name of interface is: eth1
Warning: No relative file racer.ini found, re-creating
Unable to find process to run, try re-install your process again!

Just another note to make sure we are on the same page the script file is named runracer.sh it is in the /usr/local/sbin directory. When I originally unpacked the racer.tar.gz the racer folder went to the /usr/local directory. Inside the racer folder has the racer.ini file it is talking about.

---

### Post by nixscripter on 2008-06-20
In that case, I would suggest making this the last line of the script. Instead of: ```
/usr/local/racer/ecou.sh $1
```

Do this: ```
 cd /usr/local/racer && ./ecouh.sh $1
```

The shell script appears to not look very hard for the racer.ini file.

**EDIT:** Actually, before you do that, try something simpler.

Instead of ```
dest_path=/usr/local
``` change it to ```
dest_path=/usr/local/racer
``` and see if that works. If it doesn't, try the suggestion above.

---

### Post by stvdel on 2008-06-21
Okay here are the recent tries.

Attempt #1.
Changed the script to this.

#!/bin/sh
dest_path=/usr/local/racer
export RACERC=$dest_path
/usr/local/racer/ecou.sh $1

When I tried to run it.

lai@lai-laptop:~$ cd /usr/local/sbin
lai@lai-laptop:/usr/local/sbin$ sudo runracer.sh start
All names of your net interface installed
-----------------------------------------
    eth1    0
Input one name to hace access with Internet (eth0): eth1
The name of interface is:  eth1
./racer: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
Failed to run the process
lai@lai-laptop:/usr/local/sbin$

Attempt #2
Changed the script to this.

#!/bin/sh
dest_path=/usr/local
export RACERC=$dest_path
cd /usr/local/racer && ./ecou.sh $1

When I tried to run it.

lai@lai-laptop:~$ cd /usr/local/sbin
lai@lai-laptop:/usr/local/sbin$ sudo runracer.sh start
All names of your net interface installed
-----------------------------------------
    eth1    0
Input one name to hace access with Internet (eth0): eth1
The name of interface is:  eth1
Unable to find process to run, try re-install your process again!
lai@lai-laptop:/usr/local/sbin$

Attempt#3
Changed the script to this.

#!/bin/sh
dest_path=/usr/local/racer
export RACERC=$dest_path
cd /usr/local/racer && ./ecou.sh $1

When I tried to run it.

lai@lai-laptop:~$ cd /usr/local/sbin
lai@lai-laptop:/usr/local/sbin$ sudo runracer.sh start
All names of your net interface installed
-----------------------------------------
    eth1    0
Input one name to hace access with Internet (eth0): eth1
The name of interface is:  eth1
./racer: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
Failed to run the process
lai@lai-laptop:/usr/local/sbin$ 

This is all I knew to try.

---

### Post by nixscripter on 2008-06-21
The first one is probably right.

Not finding libstdc++ is probably the result of a bad SO name. It might either be  a different version of the library (in which case it might be a big mess), or it just might mean you need a symlink somewhere.

1. Just to see if you have the library in question: ```
ls /usr/lib/libstdc++.so.5
``` If that doesn't return anything, we can only hope it's somewhere different, like /lib or /usr/gcc-**your-version**/lib.

2. Post the output of the dynamic linking dependencies of this binary: ```
ldd /usr/local/racer/race
``` This is just to verify the fact that it does require the library.

I'm starting to get the impression that whoever wrote this linux port didn't do a very good job. Normally, installers take care of this sort of thing, and their asking you to just set variables and run it as root" seems rather naiive.

---

### Post by stvdel on 2008-06-21
I ran the first code and it says cannot access because there is no file or directory. I then ran a search on the filesystem for libstdc++ and the search results returned a libstdc++.so.6 and a libstdc++.so.6.0.9 and both are located under /usr/lib although it seems there is no libstdc++.so.5. I ran the second code and it said not a dynamic executable. Yes I agree this is very poorly written and even worse when the ISP tells you yeah we have the program but no one here knows how to set it up.

---

### Post by stvdel on 2008-06-23
bump

---

### Post by nixscripter on 2008-06-23
"Not a dynamic executable?" Really? That's what I got.

The binary you posted in the compressed file seems to have been corrupted. When you run "file racer", what does it say? Does it mention corrupted ELF header? If so, you might have to try downloading/obtaining it again.

For now, I would recommend one last shot at it: go to Synaptic package manager, and install libstdc++5. That's the name of the package. Then try again. If it still doesn't work, then this might be something to talk to your ISP about (assuming they know anything, they will know "hey, your binary won't run" is a problem).

---

### Post by stvdel on 2008-06-24
Ok I installed the libst5++. Went to the terminal and got this.

lai@lai-laptop:~$ cd /usr/local/sbin
lai@lai-laptop:/usr/local/sbin$ sudo runracer.sh start
[sudo] password for lai:
All names of your net interface installed
-----------------------------------------
    eth1    0
Input one name to hace access with Internet (eth0): eth1
The name of interface is:  eth1
The process is checking your IP address, please hold on ...
ifdown: interface eth1 not configured
Ignoring unknown interface eth1=eth1.
Please Enter your LOGIN: 17110073293
Input a password: and your PASSWORD:
Can not get Requst Task, Please Check your IpTables or network, The Error message is:

Failed to run the process
lai@lai-laptop:/usr/local/sbin$ 

I don't know if it makes any difference but I am trying to do all this in ubuntu 8.04 using virtual box. Vista host with the Ubuntu guest.

---

### Post by nixscripter on 2008-06-24
> **stvdel said:**
> I don't know if it makes any difference but I am trying to do all this in ubuntu 8.04 using virtual box. Vista host with the Ubuntu guest.

That makes all the difference. I wish you have told me sooner.

Virtual guest systems have virtual interface emulation 99% of the time. eth1 is really a virtual ethernet card, being driven by the server software. What you need to figure out is how to get it an IP and how to connect it to the outside box (and world). If you can connect it there, then the outside box can deal with the ISP (using NAT or IP masquerading for the guest).

What product are you using? I don't know how VMware does it, but qemu (a linux product) I have just fought with.

Here are some general suggestions, which should be done in the linux box if you can't figure out what your configuration is on the virtual host software:

1. Run DHCP: ```
sudo dhclient -d eth1
``` and see if you get an answer from a fake DHCP server set up by your virtual host.

2. Network to nowhere, and try to get to your host box. Suppose your host box has the IP **a.b.c.d**. Try to ping it: 
```
sudo ifconfig eth1 169.254.222.1 up
sudo route add **a.b.c.d** eth1
ping -c 1 **a.b.c.d**

```

But again, there should be an option somewhere in your VM software to say "this is what networking options I want to simulate." That should get you at least to the enclosing box, if not to the entire network.

Hope this helps.

---

### Post by stvdel on 2008-06-24
Ok I did as you said, I got a response from the dhcp and also was able to ping. Let me mention what I am trying to do here. Ever since I switched ISP's, if I wanted to use the internet they make you connect through their racer program whichever OS you use. Since I could never figure out the linux racer program I had to connect to the internet using windows and the windows racer program. I downloaded the program virtual box and set up ubuntu in that because I could connect to the internet by starting up the ubuntu vitual box and it would let me connect to the internet as long as I had already started up the windows racer program and connected through that. My motive is that I don't want to use windows I only set up the virtual ubuntu in order to still have internet access and be able to test the linux racer program until I got it working so I could solely install ubuntu. I really do appreciate all the help. Thanks

---

### Post by nixscripter on 2008-06-25
Well that's the thing: you really need to have Linux running natively (i.e. in control of the hardware) if you want it to work. You would have to repartiation and install linux proper in order to test the program.

I'm glad I could help.

---

### Post by stvdel on 2008-06-25
Ok, thanks for the help. Sometime soon I will just install linux and try all the steps again.

---


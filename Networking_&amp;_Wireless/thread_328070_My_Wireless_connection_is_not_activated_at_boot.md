---
title: "My Wireless connection is not activated at boot"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by Lowfront on 2006-12-30
I'm about to delete my ubuntu partition of my laptop even though I absolutely love ubuntu.  I cannot for the life of me get my wireless to work properly.

If I do this command, I never got online untill I did this command at some point, which now do all the time trying to get online.  Even though it really doesn't seem to help. 

 sudo invoke-rc.d networking restart

then restart the computer

I have actually been online wireless a few times.  So I know its possible.  I just don't know how it happened.   All of a sudden I would be online after trying for 30 min.

Anyways I'm always connected sopposedly thats what it says on wifi radar or whatever the program is called.

dd-rt connected(none)

so I'm connected with no ip address?  Anyone please give me any advice before I go insane.  I hate needing to boot into windows to get online.  Ahhh its killing me

---

### Post by scrooge_74 on 2006-12-30
sudo ifdown  "eth1" or what ever is recognize
sudo ifup "eth1"

---

### Post by Lowfront on 2006-12-30
I LOVE YOU!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!




wow you're my hero






wow, I was ready to go insane thanks for the response.  
Now is there a way to not need to put this in every time at startup?

---

### Post by blackmh on 2006-12-30
You can try with Preferences -> Sessions

---

### Post by raul_ on 2006-12-30
Create a script that does that, make it executable and add it to System-> Preferences -> Sessions-> Startup programs

The script is just a file with those 2 commands with a .sh extension. Save it with whatever name you want and where you want. Make it executable by running "chmod +x <filenameyouchose>" and then add it to the startup programs.

IMPORTANT: Every command should end with a ;
For example, in your case you can do:

```

ifdown "eth1";
ifup "eth1";

```

Edit:

If you need to make a "sudo" command then try creating the file with sudo, like "sudo gedit internet.sh" and then "sudo chmod +x internet.sh"

---

### Post by Lowfront on 2006-12-30
> **raul_ said:**
> Create a script that does that, make it executable and add it to System-> Preferences -> Sessions-> Startup programs

The script is just a file with those 2 commands with a .sh extension. Save it with whatever name you want and where you want. Make it executable by running "chmod +x <filenameyouchose>" and then add it to the startup programs.

IMPORTANT: Every command should end with a ;
For example, in your case you can do:

```

ifdown "eth1";
ifup "eth1";

```

Edit:

If you need to make a "sudo" command then try creating the file with sudo, like "sudo gedit internet.sh" and then "sudo chmod +x internet.sh"




ok so this is what I understand

ifdown ath0;
ifup ath0;

saveitaswhatever.sh


what I don't understand

Make it executable by running "chmod +x <filenameyouchose>" and then add it to the startup programs.


If you need to make a "sudo" command then try creating the file with sudo, like "sudo gedit internet.sh" and then "sudo chmod +x internet.sh"[/QUOTE]



thanks for the help
Dave

---

### Post by raul_ on 2006-12-30
So you've saved the file. Great. now run the command 
```

chmod +x saveitaswhatever.sh

```

What I was trying to say is that those commands need to be run as root,i.e, sudo ifdown eth0, then create that file as root, i.e., "sudo gedit saveitaswhatever.sh", and then "sudo chmod +x saveitaswhatever.sh".

When this is done add the file to the startup programs (System->Preferences->Sessions) and reboot to give it a try ;)

---

### Post by Lowfront on 2006-12-31
Ok this isn't working


So I open up a text editor and write this

ifdown ath0;
ifup ath0;

save it with .sh

then

run in terminal chmod +x saveitaswhatever.sh

then add it to start list



am i missing somthing?

---

### Post by kvonb on 2006-12-31
now open a terminal, cd to wherever saveitaswhatever.sh is, then type: ```
./saveitaswhatever.sh
```

It should run.

---

### Post by kvonb on 2006-12-31
Oh, you really should make the first line this:

```
#!/bin/sh
```

and I don't think you need the ";" on the ned of the lines but I could be wrong :rolleyes:

---

### Post by Lowfront on 2006-12-31
lowfront@lowfront-x60:~$ ./network.sh
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied





I named the file network.sh

---

### Post by tseliot on 2006-12-31
I have edited the title of this thread so that it's more clear what this thread is about.

---

### Post by raul_ on 2006-12-31
> **Lowfront said:**
> lowfront@lowfront-x60:~$ ./network.sh
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied





I named the file network.sh

Did you create the file as root as i told you?

---

### Post by Lowfront on 2006-12-31
is that doing this?


chmod +x saveitaswhatever.sh

that didn't seem to do anything

---

### Post by raul_ on 2007-01-01
No. Erase the file and let's start again. 

1.
```

sudo gedit saveitaswhatever.sh

```

write the 2 commands, save it, and then

2.
```

sudo chmod +x saveitaswhatever.sh

```

3. Add the file to the startup programs and then try again

---

### Post by phossal on 2007-01-01
As you log into your system, the file .bash_profile is executed a single time. If you create a subshell, it uses .bashrc. Therefore, on a single user system, to execute the commands after successfully passing the initial login prompt (and NOT at boot time), simply insert the following commands into your .bash_profile. Note, the bash shell doesn't terminate its command lines with a semi-colon.

From the command line:
```

sudo gedit ~/.bash_profile

```

Now, copy and paste the following at the bottom. 
```

# (Copy and Paste Begin)
#The "#" Character indicates a comment line in bash.
#Start wireless
#-----------------------------------------
ifdown ath0
ifup ath0
#-----------------------------------------
#(Copy and Paste End)

```

---

### Post by Lowfront on 2007-01-03
that didn't work.....

copy and paste that hole thing right?

I try copying the hole thing then copying just #---- to #-----   and neither worked

---


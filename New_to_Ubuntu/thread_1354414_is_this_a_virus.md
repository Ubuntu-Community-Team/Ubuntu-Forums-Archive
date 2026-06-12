---
title: "is this a virus?"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by manny43 on 2009-12-13
Hello friends

avast antivirus

After scanning home directory i'm getting the following message

/home/manny/.mozila/firefox/ciuxbpjl.default/cache/2E78ADFBdol/casper/filesystem.manifest    Error while scanning 212

I dont know what it means.See if you guys can help with this issue.Thanks

---

### Post by talsemgeest on 2009-12-13
It is most likely a problem with permissions, and probably not a virus. However, just to be safe, don't execute the file (if it is executable in the first place.)

---

### Post by presence1960 on 2009-12-13
> **manny43 said:**
> Hello friends

avast antivirus

After scanning home directory i'm getting the following message

/home/manny/.mozila/firefox/ciuxbpjl.default/cache/2E78ADFBdol/casper/filesystem.manifest    Error while scanning 212

I dont know what it means.See if you guys can help with this issue.Thanks

There is no need to worry about viruses on Linux for the most part- see [here]("http://ubuntuforums.org/showthread.php?t=510812")

You might want to install rootkit software though such as rkhunter & chkrootkit.

Also enable your firewall by typing in terminal ```
sudo ufw enable
``` For a GUI frontend for ufw install gufw

all those softwares can be installed via Synaptic Package Manager or terminal by running ```
sudo apt-get install <name_of_package>
```

---

### Post by manny43 on 2009-12-13
thanks for your help. i have a question is rkhunter a command line application and if it is how do i run it
in terminal

---

### Post by presence1960 on 2009-12-13
> **manny43 said:**
> thanks for your help. i have a question is rkhunter a command line application and if it is how do i run it
in terminal

```
sudo rkhunter -c
```

For more info on options run ```
man rkhunter
```

---

### Post by manny43 on 2009-12-14
thank you very much for your help

---

### Post by running_rabbit07 on 2009-12-14
> **presence1960 said:**
> ```
sudo rkhunter -c
```For more info on options run ```
man rkhunter
```

Presence, does the man rkhunter make it run in the background?

Thanks, you are a great help to the community.

---

### Post by The_Pirate_King on 2009-12-14
"man rkhunter" will bring up the help manual for the program rkhunter. 

In general, you can "man" any program and it will give you loads of information about that program.  It's a very useful way to find your way around the command line.

---

### Post by running_rabbit07 on 2009-12-14
> **The_Pirate_King said:**
> "man rkhunter" will bring up the help manual for the program rkhunter. 

In general, you can "man" any program and it will give you loads of information about that program.  It's a very useful way to find your way around the command line.

Thanks

---


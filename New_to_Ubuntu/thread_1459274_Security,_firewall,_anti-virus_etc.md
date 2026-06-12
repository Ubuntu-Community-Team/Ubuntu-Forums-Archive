---
title: "Security, firewall, anti-virus etc"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by ambient007 on 2010-04-21
Hey guys.

I'm an Ubuntu newbie who just installed 9.10 on my laptop. 

I know that ubuntu is supposed to be a whole heap more secure than windows etc etc.

I've also read that there needs to be a few things configure/install to properly secure the system.

Would anyone care to spell it out for me?

Thanks a bunch.

---

### Post by Drenriza on 2010-04-21
Not really. Linux is pretty secure all by its own.
Aslong as your home network is secure, and you think before you do something. Their should no problems.
 
Ofcourse you can add security. For example iptables you can add rules to driffent things. (linux firewall)
 
rootkit hunter will detect backdors/malware.
 
clamav will find viruses.
 
tripwire (dont know if its free) will check that system files havnt been tampered with.
 
You got logs to tell you if intruders have tryed to come into your system or has been on your system
 
```
cat /var/log/messages |less
```
```
cat /var/log/secure |less
```
uptime can be used if you have a server, to see if the system has unexpectedly rebooted. Can be if an intruder has been their and messed something up.

---

### Post by ambient007 on 2010-04-21
> **Drenriza said:**
> Not really. Linux is pretty secure all by its own.
Aslong as your home network is secure, and you think before you do something. Their should no problems.
 
Ofcourse you can add security. For example iptables you can add rules to driffent things. (linux firewall)
 
rootkit hunter will detect backdors/malware.
 
clamav will find viruses.
 
tripwire (dont know if its free) will check that system files havnt been tampered with.


Are these things that I would find using synaptic?
 
> 
You got logs to tell you if intruders have tryed to come into your system or has been on your system
 
```
cat /var/log/messages |less
``````
cat /var/log/secure |less
```uptime can be used if you have a server, to see if the system has unexpectedly rebooted. Can be if an intruder has been their and messed something up.

I don't have a server and I don't know a thing about logs...thanks for your help though.

---

### Post by HarrisonNapper on 2010-04-21
Theoretically, uptime could be used just to see what it is in general, so that applies to home environments as well. I agree that occasionally looking at the message and security logs is a good idea. I have a little widget in KDE that just runs "tail -f /var/log/messages" all of the time.

ClamAV you will find in Synaptic and there are a number of decent AV programs out there that you won't find in synaptic. It's probably a good idea to have some anti-virus protection anyway. True, it's a rare thing (incredibly) in the linux world, but none is better than incredibly rare. Well, none in theory. You can also install Firestarter if you want a nice front-end to iptables.

---

### Post by jmszr on 2010-04-21
ambient007,

This should be of interest to you: [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) .

---

### Post by Drenriza on 2010-04-21
If you think somebody has cracked his way into your system. And you are by the system then the tail command is gold.
 
```
tail -f -n20 /var/log/messages
```
```
tail -f -n20 /var/log/secure
```
 
Since this will give you a live log with the 20 newest lines added to the log.
 
also a good tool can be analysis console. Can analyze log files. And detect if an intrusion is taking place.
 
also getting an encryption algorythim to encrypt your log files & your password files /etc/passwd, /etc/shadow for users
and /etc/groups, /etc/gshadow
 
will give x-tra protection. The blowfish algorythem is an option.

---

### Post by ubunterooster on 2010-04-21
[color=blue]Turn on firewall: ```
sudo ufw enable
```
With AV you are more likely to remove an important part of your system due to false positives than to catch malware. Oh, and remember to[/color][color=red]back up everything[/color]

---

### Post by 3rdalbum on 2010-04-21
> **ambient007 said:**
> Hey guys.

I'm an Ubuntu newbie who just installed 9.10 on my laptop. 

I know that ubuntu is supposed to be a whole heap more secure than windows etc etc.

I've also read that there needs to be a few things configure/install to properly secure the system.

Would anyone care to spell it out for me?

Thanks a bunch.

Well, there's not really anything you need to do to properly secure the system. There's no listening ports by default, so you don't need a personal firewall. There's no Linux viruses in the wild, so you don't need antivirus. Because your system is currently not listening to any ports, there's no chance of getting a rootkit, so you don't need an anti-rootkit program.

---

### Post by ed-koala on 2010-04-21
I've run Ubuntu for several years without adding any security and never had a single problem.  I doubt you need it unless you knowingly engage in high-risk behavior that lets people onto your system.

---

### Post by kishorr on 2010-04-21
i have a decade old comp, runnin on ubuntu 5.04 how can i keep my comp secure??i haven heard of AV for linux:confused:

---

### Post by ubunterooster on 2010-04-21
> **kishorr said:**
> i have a decade old comp, runnin on ubuntu 5.04 how can i keep my comp secure??i haven heard of AV for linux:confused:
Upgrade. You may need to go to a lighter Desktop Enviroment. Try Lubuntu (after the 29th)or Xubuntu

---

### Post by Homicide on 2010-04-21
> **ed-koala said:**
> I've run Ubuntu for several years without adding any security and never had a single problem.  I doubt you need it unless you knowingly engage in high-risk behavior that lets people onto your system.

+1

I'm constantly astounded by people who complain about system errors and then tell me about these neat custom cursors they downloaded from 'the internet explorer.'

Also, would a firewall be recommended if you do some light torrenting (1-2 times a week)?

---

### Post by ubunterooster on 2010-04-21
[color=blue]Better safe then sorry. It's an oft debated topic [whether a firewall is needed] but I go towards "overly safe" [if possible] [/color]

---

### Post by HarrisonNapper on 2010-04-21
> **ed-koala said:**
> I've run Ubuntu for several years without adding any security and never had a single problem.  I doubt you need it unless you knowingly engage in high-risk behavior that lets people onto your system.

The ultimate question is if you did have a problem, would you know? If you have a screenscraper running at startup or a keylogger forwarding every keystroke to someone, it doesn't result in a popup window or anything noticeable. However, I agree that in general, Linux users are more aware of their environment and compared to the feasibility of writing malware for Linux (yes, it can be done), it becomes almost not worth it to set up anything too complex.

@ubunterooster: I completely agree with everything you said. The risk of deleting useful files from false positives (PUAs, anyone?) is much higher than catching a virus. I also agree with "better safe than sorry" when it comes to firewall. A firewall might slow down your torrenting, but on any kind of tor network like that, it's probably a good idea to keep it around.

---

### Post by ambient007 on 2010-04-22
Could someone please define 'high risk behaviour' and 'listening ports' for me?

---

### Post by Drenriza on 2010-04-22
High risk behavior (in my opinion) could for example.
 
That you do all tasks on your system as the root user.
 
You use telnet. 
 
You don't upgrade your system. 
 
you give files & directoryes 777 permissions. 
 
The (.) "your current working directory" should never be in your path variable. ```
echo $PATH
``` and i also think ```
pwd
``` command will show it.
To explain this abit.
 
Copyed from [http://www.linuxforums.org/forum/debian-linux-help/57694-changing-path-variable.html](http://www.linuxforums.org/forum/debian-linux-help/57694-changing-path-variable.html): 
it is recommended that the working directory should never be put first in your PATH. One could accidentally execute a command in the working directory that masks an common command. For example, if an executable named ls exists in the working directory then it would be executed instead of the ls command in the /bin directory. This could have disasterous effects, especially if you are superuser and the ls command was placed there malicously.
 
Just some examples.

---

### Post by ubunterooster on 2010-04-22
Listening ports is most easily defined by analogy: Your computer is a military harbor. Listening "ports" are ports which are wide open for anyone who knows to look.


Also risky behaviour, editing your repositories without researching what you are adding.

---

### Post by 3rdalbum on 2010-04-22
> **kishorr said:**
> i have a decade old comp, runnin on ubuntu 5.04 how can i keep my comp secure??

Ubuntu 5.04 is end-of-life and hasn't had any security updates for years. You really should upgrade it. You're still probably pretty safe as long as you have a firewall or don't have any services listening on incoming ports, but it is possible for somebody to craft a malicious video file or PDF to attack your computer when you open it. Those security flaws have long since been patched in later versions of Ubuntu.

---

### Post by fuzzylogic on 2010-05-01
I have ubuntu 9.10. When I type in my "messenger messages to someone it goes to them that they have virus, so how do I resolve this? I also think someone hack into my computor because they got into my game server so I can't access. What can I do to fix all this? Im new on this.

---

### Post by kishorr on 2010-05-02
> **ubunterooster said:**
> Upgrade. You may need to go to a lighter Desktop Enviroment. Try Lubuntu (after the 29th)or Xubuntu
yah, have to upgrade, rite now on 9.10 Karmic..., have upgraded the ram, its working fine, thanks for the suggestion

---

### Post by Primefalcon on 2010-05-02
Ubuntu ships secure with all ports closed. It using Iptables or is it apparmour now? either way your safe...

if you want to open ports for certain programs or services just install firestarter it's a good front end to the back end firewalls that are built-in to Ubuntu

for info there is a good antivirus for Ubuntu, thing is it's more for scanning for windows viruses, for scanning stuff before you send them onto your windows friends, those viruses are inert.. useless under Linux... it's called clam av, there is a gui front end for it called clam tk as well, it's very good, but as I said it's more just to protect windows users you might send stuff too

Ubuntu has a very secure security model apart from just the firewall, 1 being any system wide changes needs root powers, for which there is sudo.... nothing can execute unless you specifically give it execute permissions

---

### Post by rcktsingh on 2010-05-10
> **ed-koala said:**
> i've run ubuntu for several years without adding any security and never had a single problem.  I doubt you need it unless you knowingly engage in high-risk behavior that lets people onto your system.

+1

---

### Post by HarrisonNapper on 2010-05-12
> **rcktsingh said:**
> +1

Take a look at the first part of what I wrote on page two. There's a difference between having a problem and knowing that you have a problem.

In any case, the weakest part of any system will always be the user, no matter how much security the system itself has.

Take an example: Person A wants to install program B, so they do a search and download a script to have it installed for them. In this case, A runs it as root and in addition to installing the program, it also installs and configures openssh and adds a user who is allowed access from any IP and who has root or admin privileges. Maybe it also installs a keylogger that emails keystrokes at terminal password prompts to the creator, who knows. Would you know if ssh was running, if the perpetrator had accessed your system and jotted down your bank account information? Nothing would show on your screen and the program you intended to install did, in fact, install, so who's to say that it was any different?

Edit: I'm not addressing you as an individual in this case. I even think that for a Desktop system, it really isn't necessary to do too much. Just to be mindful of one's own actions and know which logs to check. What disturbs me is the trend of implying that the security of an OS is inversely related to the number of people who think they have or have had a virus on it.

---


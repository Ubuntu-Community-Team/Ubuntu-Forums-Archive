---
title: "Re-install on dual booting MBP"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by GLMantra663 on 2011-02-11
So ive somehow messed up my root privileges on my macbook pro which is dual booting osx 10.6 and ubuntu 10.10. When I try to run synaptic I get the error message:

'Failed to run /usr/sbin/synaptic as user root'
'The underlying authorization mechanisim (sudo) does not allow you to run this program. Contact the system administrator.'

Im also unable to run a 'sudo' command in Terminal.

I've searched high and low for a fix but I cant find anything that gives a complete fix except re-install. Im fine with re-installing as I have no data on this partition that would wreck my life to loose. But I dont know how to re install. When I try to boot from my DVD I get the rEFit menu showing my osx partition and my linux partition but no boot from cd/dvd option. Would i have to go into osx and delete my linux partition and just install as i did before? This is the only way i could think of but im just asking the gurus here before i go for it.

---

### Post by cariboo on 2011-02-11
Check to see if your user is a member of the following groups:

```
cariboo@chilanko:~$ groups
cariboo adm dialout cdrom plugdev lpadmin admin sambashare
```

if your are missing any of the groups, you can add yourself back using the following command:

```
sudo gpasswd -a <your user name> adm
```

---

### Post by GLMantra663 on 2011-02-11
> **cariboo907 said:**
> Check to see if your user is a member of the following groups:

```
cariboo@chilanko:~$ groups
cariboo adm dialout cdrom plugdev lpadmin admin sambashare
```if your are missing any of the groups, you can add yourself back using the following command:

```
sudo gpasswd -a <your user name> adm
```

already tried that im only a member of my group that takes the same name as my user name, and i cant run a command with sudo because im not a 'sudoer'.

---

### Post by GLMantra663 on 2011-02-12
found a fix. to anyone else who has this problem

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

theres multiple fixes for different cases of brokensudo.

---


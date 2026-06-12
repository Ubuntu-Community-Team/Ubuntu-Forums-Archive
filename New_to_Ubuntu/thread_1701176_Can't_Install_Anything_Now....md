---
title: "Can't Install Anything Now..."
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Singer on 2011-03-06
friends
i cant install any new software from Ubuntu Software Center
the error (in the attachment) comes up always
any ideas on how to overcome???
Thanks in Advance
Singer

---

### Post by ikt on 2011-03-06
> **Singer said:**
> friends
i cant install any new software from Ubuntu Software Center
the error (in the attachment) comes up always
any ideas on how to overcome???
Thanks in Advance
Singer

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/705988](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/705988)

To overcome it use apt on the command line.

Applications > Terminal

To update your sources:
sudo apt-get update

To upgrade your system:
sudo apt-get upgrade

To install an application:
sudo apt-get install x

Something else that has worked for some people:

If you System->Administration-> Synaptic > Settings > repositories > and change the "Download From" and select another server it may fix it.

---

### Post by grahammechanical on 2011-03-06
What happens when you click OK?

You are being asked to give your approval. The program may be in the Ubuntu Software Centre but it is not produced by Canonical and the download is not coming from servers that Canonical will take responsibility for.

If you do not trust the source of this program (and I see that it is the Gnome Universal Firewall which many, many people trust), then do not download the program. You are being given the choice. I think that this is the polite thing for the Software Centre to do.

Regards.

---

### Post by xptional on 2011-03-06
Hi :),

are you using any proxy ? if yes, may be it trouble you installing softwares ...  May below link help you,

[http://ubuntuforums.org/showthread.php?t=83401]("http://ubuntuforums.org/showthread.php?t=83401")

If not, then please upload output of this code in the terminal,
```
sudo apt-get install update
```

---

### Post by Singer on 2011-03-07
> **grahammechanical said:**
> What happens when you click OK?

You are being asked to give your approval. The program may be in the Ubuntu Software Centre but it is not produced by Canonical and the download is not coming from servers that Canonical will take responsibility for.

If you do not trust the source of this program (and I see that it is the Gnome Universal Firewall which many, many people trust), then do not download the program. You are being given the choice. I think that this is the polite thing for the Software Centre to do.

Regards.

when i click ok it goes back to the same window as before without installing anything and thats the trouble ;).

---

### Post by beew on 2011-03-07
Have you tried using Synaptic instead? (System > Administration > Synaptic Package Manager), I never use the Software Center to install programs, always use Synaptic and I never have a problem.

---

### Post by Singer on 2011-03-07
> **xptional said:**
> Hi :),

are you using any proxy ? if yes, may be it trouble you installing softwares ...  May below link help you,

[http://ubuntuforums.org/showthread.php?t=83401]("http://ubuntuforums.org/showthread.php?t=83401")

If not, then please upload output of this code in the terminal,
```
sudo apt-get install update
```

no dear i am not using a proxy as it is a personal laptop. 
i tried the code given above and these are the results 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package update

```

---

### Post by vivek.pandey on 2011-03-07
the command is sudo apt-get update and not sudo apt-get install update..
update is not a package that can be installed

---

### Post by vivek.pandey on 2011-03-07
there are certain softwares in ubuntu which show such errors
have a look here

---


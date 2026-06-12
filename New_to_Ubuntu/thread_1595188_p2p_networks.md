---
title: "p2p networks"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by Legeril on 2010-10-13
I've always avoided p2p programs because of the high risk of virus's but what are they like using with Linux? Does Linux have it's own p2p networks? Are there any programs/networks that are recommended? What are the security issues I should take into consideration if I use a p2p  program?

---

### Post by jtarin on 2010-10-13
Virtually no problems....only if you download a virus harmful to a Windows system then transfer that file to a Windows environment.

---

### Post by Legeril on 2010-10-13
A friend told me to download a program called giFT, I just downloaded it through the Synaptic Package Manager and installed it. But I can't find the program, how do I find out where it's been installed too? And where I am able to run it from?

---

### Post by jtarin on 2010-10-13
If it installed you should be able to find it by going to the terminal and issuing the command ```
sudo updatedb
``` let it run until finished....it updates you data base of all files on your installation. Then issue the command ```
sudo locate <application name>
``` in your particular case replace <application name> with "gift" without quotation marks.You then be able to find all instances of the application on yourinstall. Have you tried simply looking through the Main menu?

---

### Post by spikoley on 2010-10-13
The *which* command will also tell you where the command is installed.

```
which command-name
```

You can add it to the menu by right clicking on Applications and then click Edit Menus.

---

### Post by cascade9 on 2010-10-13
> **Legeril said:**
> I've always avoided p2p programs because of the high risk of virus's but what are they like using with Linux? Does Linux have it's own p2p networks? Are there any programs/networks that are recommended? What are the security issues I should take into consideration if I use a p2p  program?

Its not so much the actual program that has a risk of viruses (though that can happen), its more what you d/l. D/ling a file, eg a .exe that has some sort of malware, and running it on windows would be enough to get you infected, no matter what OS it was d/led on. 

No 'linux only' p2p netwoprks as far as I know, but there are linux clients for almost all of them. BTW, giFT is just a single program that interfaces with multipule p2p networks, and from what I've heard, does none of them as well as a client made for just that network. 

As for what network is recommended...depends on what your after. Some of them are good for 1 thing, hopeless for another.....

---


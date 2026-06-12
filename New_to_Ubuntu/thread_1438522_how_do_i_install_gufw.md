---
title: "how do i install gufw?"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by sanjaypothen on 2010-03-25
I went to the help&support of ubuntu9.10,then went to the set firewall section and clicked the"install Gufw",but the message shown was that the package is not found.

                                     How do i install the gufw so as to get the computer sytem & internet surfing safe.

                                  In the system<administration<firewallconfigration  , (Here i could not find "firewallconfigration")

                               Since i am a new user with less knowledge i would like to use gufw.Is there a solution?

---

### Post by cdenley on 2010-03-25
```

sudo apt-get update
sudo apt-get install gufw

```

If that fails post the full output, as well as this output.
```

grep "^[^#]" /etc/apt/sources.list /etc/apt/sources.list.d/*.list

```

By the way, a firewall does nothing to protect your internet surfing.

---

### Post by sanjaypothen on 2010-03-25
> **cdenley said:**
> ```

sudo apt-get update
sudo apt-get install gufw

```If that fails post the full output, as well as this output.
```

grep "^[^#]" /etc/apt/sources.list /etc/apt/sources.list.d/*.list

```By the way, a firewall does nothing to protect your internet surfing.


Well i don't understand by the "post full output"?

---

### Post by cdenley on 2010-03-25
> **sanjaypothen said:**
> Well i don't understand by the "post full output"?

When you run a command, it usually produces output, or text that appears in the terminal which the command is run within. You can then copy and paste that output into a post in this thread. That would provide us with more information so we can determine what your problem is.

---

### Post by sanjaypothen on 2010-03-25
pl. advise how to install gufw? I could not install it as the package was not available ! pl. help fast!!

---

### Post by wojox on 2010-03-25
Open Synaptic Package Manager and search for it. It's in there.

---

### Post by Paddy Landau on 2010-03-25
What version of Ubuntu do you have?

I have 8.04 and it's not in the repository. But I've just checked a 9.04 machine, and it is there.

BTW, are you sure that you need to change the firewall settings? The default settings are pretty robust for most installations -- mine checks out better than Windows did with a paid-for firewall.

---

### Post by sanjaypothen on 2010-03-25
> **cdenley said:**
> When you run a command, it usually produces output, or text that appears in the terminal which the command is run within. You can then copy and paste that output into a post in this thread. That would provide us with more information so we can determine what your problem is.
[B]When typed the command

sudo apt-get update

            All the information came was about  sites (Karmic updates,ubuntu.com) and all was the connection failed messages(ip  addresses was given)

When typed the command

sudo apt-get install gufw

Output was: Reading packages list-----Done
                    Building dependency tree
                    Reading state information-----Done
                    E: couldn't find package gufw

[I]PL.Note
 --------
[/I]                  I have installed the ubuntu9.10 cd from cononical. Since the gufw installation was not confirmed, i haven't used the ubuntu9.10 for netsurfing.I am only at present using the windows os.(Through dual autumatic partion ) I think the first sudo command was because the network was not conneted(As i am not sure of the gufw installation,i did not connect to the net in the ubuntu9.10 os) 

                    I want to first enable the gufw the only i would be confident to connect to the internet through the ubuntu9.10 os. Please help fast with a solution
    
[/B]

---

### Post by ublintu on 2010-03-25
Hi,

ufw is the same, but no graphical interface:  [http://ubuntuforums.org/showthread.php?t=823741&highlight=ufw+enable](http://ubuntuforums.org/showthread.php?t=823741&highlight=ufw+enable)

---

### Post by sanjaypothen on 2010-03-25
> **cdenley said:**
> When you run a command, it usually produces output, or text that appears in the terminal which the command is run within. You can then copy and paste that output into a post in this thread. That would provide us with more information so we can determine what your problem is.

[QUOTE=sanjaypothen;9027207][B]When typed the command

sudo apt-get update

            All the information came was about  sites (Karmic updates,ubuntu.com) and all was the connection failed messages(ip  addresses was given)

When typed the command

sudo apt-get install gufw

Output was: Reading packages list-----Done
                    Building dependency tree
                    Reading state information-----Done
                    E: couldn't find package gufw

[I]PL.Note
 --------
[/I]                  I have installed the ubuntu9.10 cd from cononical. Since the gufw installation was not confirmed, i haven't used the ubuntu9.10 for netsurfing.I am only at present using the windows os.(Through dual autumatic partion ) I think the first sudo command was because the network was not conneted(As i am not sure of the gufw installation,i did not connect to the net in the ubuntu9.10 os) 

                    I want to first enable the gufw the only i would be confident to connect to the internet through the ubuntu9.10 os. Please help fast with a solution
    
[/B]

---

### Post by sanjaypothen on 2010-03-25
I went there.it is no there.pl.help any one!!!!

---

### Post by sanjaypothen on 2010-03-25
> **Paddy Landau said:**
> What version of Ubuntu do you have?

I have 8.04 and it's not in the repository. But I've just checked a 9.04 machine, and it is there.

BTW, are you sure that you need to change the firewall settings? The default settings are pretty robust for most installations -- mine checks out better than Windows did with a paid-for firewall.

i am using ubuntu 9.10

---

### Post by bodhi.zazen on 2010-03-25
You can enable your fiewall in one step , from the command line:

```
sudo ufw enable
```

This will have the same effect as installing and enabling your firewall in gufw.

If you want to install gufw you need to enable a few repositories, gufw is in Universe

See : [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by sanjaypothen on 2010-03-25
> **wojox said:**
> Open Synaptic Package Manager and search for it. It's in there.
I have gone there it is not there!!

---

### Post by wojox on 2010-03-25
> **sanjaypothen said:**
> I have gone there it is not there!!

You open Synaptic System > Administration > Synaptic Package Manager

Type in **gufw** into the search box and it's not there?

---

### Post by bodhi.zazen on 2010-03-25
> **sanjaypothen said:**
> I went to the help&support of ubuntu9.10,then went to the set firewall section and clicked the"install Gufw",but the message shown was that the package is not found.

                                     How do i install the gufw so as to get the computer sytem & internet surfing safe.

                                  In the system<administration<firewallconfigration  , (Here i could not find "firewallconfigration")

                               Since i am a new user with less knowledge i would like to use gufw.Is there a solution?

... merged your two threads. Please do not start multiple threads on the same topic, it leads to duplication of effort and confusion.

Please see my earlier post : [http://ubuntuforums.org/showpost.php?p=9027280&postcount=13](http://ubuntuforums.org/showpost.php?p=9027280&postcount=13)

[http://packages.ubuntu.com/karmic/gufw](http://packages.ubuntu.com/karmic/gufw)

---

### Post by durand on 2010-03-25
You don't need to use a firewall on ubuntu. Gufw is just a gui for ufw, which is a frontend to iptables, a firewall built into linux. You can safely surf the internet without "enabling" gufw, which is mainly used for opening ports if you are running a server on your computer.

---

### Post by sanjaypothen on 2010-03-25
> **wojox said:**
> You open Synaptic System > Administration > Synaptic Package Manager

Type in **gufw** into the search box and it's not there?
NO!! any other way?

---

### Post by oldos2er on 2010-03-25
"I think the first sudo command was because the network was not conneted(As i am not sure of the gufw installation,i did not connect to the net in the ubuntu9.10 os)"

apt-get and Synaptic require a net connection to function. 

You might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) and in particular the subheading 'The Windows Mindset'.

---

### Post by durand on 2010-03-25
Try this:
Open a terminal (Applications > Accessories > Terminal)
Type this:
```
sudo apt-get update
apt-cache search gufw
```

The package database should then update over the internet and you should get something like this at the end:
```
gufw - graphical user interface for ufw
```

If you don't, type this into the terminal:
```
cat /etc/lsb-release
```

Finally, if you do get gufw showing up, type this to install it:
```
sudo apt-get install gufw
```

or click [here]("apt:gufw") and it will auto install.

---

### Post by d3v1150m471c on 2010-03-25
Try firestarter before you get too comfortable with (g)ufw. It's a "dead project" which means virtually nothing considering all it's designed to do is alter iptables from a GUI. This is the same as (g)ufw only with more options and arguably better security.

---

### Post by cdenley on 2010-03-25
> **sanjaypothen said:**
> 
All the information came was about  sites (Karmic updates,ubuntu.com) and all was the connection failed messages(ip  addresses was given)


We need the actual output, not your summary. It sounds like you don't have an internet connection, or are failing to connect to the repositories.

In addition to the actual output, post the output from this command.
```

grep "^[^#]" /etc/apt/sources.list /etc/apt/sources.list.d/*.list

```

and also this command
```

nc -z -v security.ubuntu.com 80

```

---

### Post by d3v1150m471c on 2010-03-25
Make sure you have the appropriate software sources enabled then:
```

sudo apt-get update

```
relaunch synaptic and it will be there.

---

### Post by marquinos on 2010-03-26
Hi!
You can download from the official web:
[https://launchpad.net/gui-ufw/+download](https://launchpad.net/gui-ufw/+download)
Choose the same version as your Ubuntu version ;)

For install, 2 clicks into the file .deb and enter your administrative password ;)
Best regards!

---

### Post by Paqman on 2010-03-26
> **bodhi.zazen said:**
> 
If you want to install gufw you need to enable a few repositories, gufw is in Universe


Just bumping this, as it seems to have slipped under the radar somehow. Make sure you've got the "Universe" repo checked in your Software Sources. If you have, you can get gufw from Synaptic.

You don't need gufw for browsing though. The default install is perfectly safe.

---

### Post by 3rdalbum on 2010-03-26
Interesting how nobody seems to have picked up, the original poster doesn't seem to know what a firewall actually does.

Listen. First off, the reason why gufw doesn't appear in Synaptic is because you haven't retrieved the package list. It's simple: Go into Synaptic Package Manager and click the Reload button. This will retrieve the information about what packages are available.

Now, BEFORE you go installing gUFW, you probably don't need it. Bear with me:

A firewall is a piece of software that prevents programs on your computer from recieving *incoming* connection requests. You need a firewall on Windows, because by default on Windows there are programs that will listen for incoming connections, and attackers can take advantage of this.

On Ubuntu, however, by default NO programs listen for incoming connections. If they're not listening, they can't be remotely attacked even without a firewall. If you were running a web server or Samba server, then those programs would be listening; but they are not present in the default Ubuntu install, and besides if you were running those programs then you wouldn't want a firewall preventing access to them.

If you already have a **broadband** (ADSL/cable) modem that your computer is connected to (wired or wirelessly) then your whole network is **already** protected by a firewall, and you don't need to run one on your computer.

If you **don't** have any programs running on your computer that are listening for **incoming** connections, then you **don't** need a firewall on your computer.

If you are running a web server as a test and you don't want ANY other computers to access it, then you want a personal firewall.

I'll also address another misconception about firewalls. Some people think that an incoming connection is the same as an outgoing connection - i.e. that if you're surfing the web on Firefox, that this opens an incoming port and you need a firewall. This is not true. Web browsers, IM applications and e-mail clients do not listen for incoming connections, they only initiate outgoing connections. A firewall will not help protect you when you're web surfing, because it's a totally different thing.

**In short, just to be completely clear:**

It's safe for you to connect to the Internet and do your web surfing without a firewall, on Ubuntu. It's not on Windows, but it is on Ubuntu. And if you are connected to a modem through an Ethernet cable or Wifi, then you already are behind a firewall.

If you STILL want a firewall, then gUFW is a great program for configuring it. You just need to hit the Reload button in Synaptic to get the contents of the repositories from the Internet.

---

### Post by cdenley on 2010-03-26
> **3rdalbum said:**
> Interesting how nobody seems to have picked up, the original poster doesn't seem to know what a firewall actually does.

I did in the first reply.
> **cdenley said:**
> 
By the way, a firewall does nothing to protect your internet surfing.

---


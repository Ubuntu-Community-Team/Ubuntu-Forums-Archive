---
title: "How to activate root priviledges using terminal?"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by listerdl on 2010-04-04
Hi is there a way to ensure that i am using root privilidges using the terminal?

I am often told by terminal that I must have "root priviledges"

thanks

---

### Post by sisco311 on 2010-04-04
Simply prepend sudo to all the commands you would normally run as root.

See: [uhelp]community/RootSudo[/uhelp]

---

### Post by s_ø on 2010-04-04
type sudo before the command. You will promted for your password.
read about sudo here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by snowpine on 2010-04-04
*(edit: removed dangerous suggestion)*

---

### Post by blur xc on 2010-04-04
> **snowpine said:**
> In addition to the excellent advice above, if you have to type a whole bunch of commands as root:

```
sudo -i
```When you are done, type: 

```
exit
```to return to your regular user privileges. :)

I have a very customized .bashrc with lots of special functions and aliases- and when I use sudo -i I lose all of those.  Apparently is loads the root's .bashrc or some default profile...  If I enter "sudo bash", I get to keep my .bashrc settings in a root terminal...

BM

---

### Post by cdude42 on 2010-04-04
> **sisco311 said:**
> Simply prepend sudo to all the commands you would normally run as root.

See: [uhelp]community/RootSudo[/uhelp]

for example ```
 sudo apt-get install program 
```

instead of ```
 apt-get install program 
```

---

### Post by fromthehill on 2010-04-04
> **blur xc said:**
> I have a very customized .bashrc with lots of special functions and aliases- and when I use sudo -i I lose all of those.  Apparently is loads the root's .bashrc or some default profile...  If I enter "sudo bash", I get to keep my .bashrc settings in a root terminal...

BM
copy your .bashrc to the '/root' directory

---

### Post by listerdl on 2010-04-04
great thanks! Amazing support

---

### Post by blur xc on 2010-04-05
> **fromthehill said:**
> copy your .bashrc to the '/root' directory

Is there a reason that sudo -i is better than sudo bash to start a root terminal?

If not- sudo bash seems simpler than having to remember to copy my .bashrc over the /root every time I make a change to it.

BM

edit- also it seems that sudo -i makes /root your home folder ($HOME variable) while sudo bash leaves your home folder alone...  Dunno if that's good, bad, or indifferent though.

---

### Post by da burger on 2010-04-05
I believe ```
sudo -i
``` means all your commands are carried out as if you are root where as ```
sudo bash
``` carries out the commands as you but with root privileges.

---

### Post by blur xc on 2010-04-05
> **da burger said:**
> I believe ```
sudo -i
``` means all your commands are carried out as if you are root where as ```
sudo bash
``` carries out the commands as you but with root privileges.

That's facinating- but what are the pros and cons of using one over the other, besides what I've already mentioned?

I'm really wondering what's the better way-

Thanks,
BM

---

### Post by lisati on 2010-04-05
> **blur xc said:**
> That's facinating- but what are the pros and cons of using one over the other, besides what I've already mentioned?

I'm really wondering what's the better way-

Thanks,
BM

Have a look here: [http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

---

### Post by sisco311 on 2010-04-05
> **blur xc said:**
> Dunno if that's good, bad, or indifferent though.

If you know the [differences]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4"), then you can choose the one which suits you more...

For new users, I always suggest *sudo command* & I post a link to the community documentation from where, if they want, they can learn more about sudo.

Regarding of *sudo -i*, from the community doc:

*Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as root.*

---

### Post by blur xc on 2010-04-05
> **sisco311 said:**
> If you know the [differences]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4"), then you can choose the one which suits you more...

For new users, I always suggest *sudo command* & I post a link to the community documentation from where, if they want, they can learn more about sudo.

Regarding of *sudo -i*, from the community doc:

*Please do not suggest this to others unless you personally are available 24/7 to support the user if they have issues as a result of running a shell as root.*

Fantastic- that's exactly what I was looking for.  sudo -i is the "safer" method of getting a root terminal.  Not that I ever really use a root terminal for anything, but it's good to know.  Just like knowing the difference between gksu and sudo for graphical apps. 

thanks,
BM

---


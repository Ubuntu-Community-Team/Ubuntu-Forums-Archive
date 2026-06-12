---
title: "root password"
date: 2010-06-16
forum: New to Ubuntu
---

### Post by chrisvk on 2010-06-16
When I su in the command window and it asks for the root password I insert my user password and it gives me an authentication error. I'm using Ubuntu 10.04 and am the sole user. When I set up, I entered my password under administrator, but it doesn't seem to recognise this password as root. I'm trying to load some software which requires me to log in as root. What should I do?

---

### Post by bodhi.zazen on 2010-06-16
Ubuntu uses sudo, use

```
sudo -i
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Chesamo on 2010-06-16
You can also use ```
sudo su
``` but I'd recommend sudo -i.

---

### Post by doas777 on 2010-06-16
I'm not sure what is  up with su, as I don't use it often, but ubuntu doesn;t use the root account by default. being an "administrator" by their parlance, is being a standard user, unless you use sudo/gksu to invoke a command with root privledges. the password you give it is your own login, not a different users.

sudo is a cli utlity that you just put at the  begining of each command
```

sudo <command + opt/args>

```
if you want to run a series of commands as root, use 'sudo -s' and type exit when done. 

gksu is the same as sudo, but for gui apps.

---

### Post by Bachstelze on 2010-06-16
> **doas777 said:**
> 
if you want to run a series of commands as root, use 'sudo -s' and type exit when done. 

sudo -i, please, not sudo -s. sudo -s retains the environment of the user who called it, which can have quite nasty implications if you expect otherwise (for example, the commands run as root will be visible in the user's shell history file).

---

### Post by sidzen on 2010-06-16
Simply use:
[PHP]history -c && rm -f ~/.bash_history[/PHP]before either 
[PHP]init 0[/PHP] to shutdown, or
[PHP]init 6[/PHP] to reboot!

---

### Post by wojox on 2010-06-16
> **sidzen said:**
> Simply use:
[PHP]history -c && rm -f ~/.bash_history[/PHP]before either 
[PHP]init 0[/PHP] to shutdown, or
[PHP]init 6[/PHP] to reboot!

Or you could just use 

```
sudo -i
```

As stated above.

---

### Post by sidzen on 2010-06-16
> **wojox said:**
> Or you could just use 

```
sudo -i
```

As stated above.
I like your tagline, wojox!
Also love the give and take.

---

### Post by wojox on 2010-06-16
> **sidzen said:**
> I like your tagline, wojox!
Also love the give and take.

Tagline = Stone Temple Pilots. :p

---

### Post by karthick87 on 2010-06-16
What is the difference between [COLOR=Navy]sudo su[/COLOR] and[COLOR=Navy] sudo -i[/COLOR]

---

### Post by Serpher on 2010-06-16
> **getyourkarthick said:**
> What is the difference between [COLOR=Navy]sudo su[/COLOR] and[COLOR=Navy] sudo -i[/COLOR]

su swtiches your actual user, while sudo -i has the same effect but for the lack of a better term it's like a virtual su. sudo runs a single command as root without switching users.

---

### Post by bodhi.zazen on 2010-06-16
> **getyourkarthick said:**
> What is the difference between [COLOR=Navy]sudo su[/COLOR] and[COLOR=Navy] sudo -i[/COLOR]

> **Serpher said:**
> su swtiches your actual user, while sudo -i has the same effect but for the lack of a better term it's like a virtual su. sudo runs a single command as root without switching users.

The differences are moderately technical :

[Difference between sudo su and sudo -s]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4")

---

### Post by xsandz on 2010-06-17
There is a subtle difference between two commands -- "su" and "sudo"..."su"---stands for "Switch User" and "sudo" stands for "Switch User and DO (any operation u might want to perform to be in that particular user mode)" . So while you are using the command "su"...you will have to authenticate yourself with the credential information of that particular user. But if u use "sudo", then you don't have to authenticate yourself with the credentials of that particular user ...because you will not be logged into the system as the switched user whereas u will just perform the particular task in that user mode and after completion of the task you will get back to your normal user mode.

---

### Post by karthick87 on 2010-06-17
Thank you,very useful information :)

---


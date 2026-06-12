---
title: "run connky at starting using root permission"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by davegt72 on 2011-05-10
I have recently been playing around with conky, and I love it. Currently, I have it set to load upon startup, but without root permissions it will not display my current ESSID or signal strength. I am the only user on my computer, so I am the admin. Does anyone know of a script I could write to make this work?

Thanks!

---

### Post by TheNerdAL on 2011-05-10
Maybe this might work: [http://www.wikihow.com/Become-Root-in-Ubuntu](http://www.wikihow.com/Become-Root-in-Ubuntu)

---

### Post by davegt72 on 2011-05-10
> **TheNerdAL said:**
> Maybe this might work: [http://www.wikihow.com/Become-Root-in-Ubuntu](http://www.wikihow.com/Become-Root-in-Ubuntu)
This may work if I can figure out how to set a startup program from the command line. Any help with that?

---

### Post by Dondermans on 2011-05-10
I did not write this script myself (instead I got it from the topic called [_Post your .conkyrc files w/ screenshots_]("http://ubuntuforums.org/showthread.php?t=281865") if my memory serves me well).

```
#!/bin/bash
sleep 4;
exec conky
exit
```I suppose it should execute Conky as root when adapting it as follows:

```
#!/bin/bash
sleep 4;
exec sudo conky
exit
```The [sleep 4;] parameter delays execution to make sure Conky appears against my desktop background instead of the purple login screen which is shown for a few seconds after one provides the credentials. I am not in the habit of posting untested solutions, but I cannot test it since I do not have got wireless internet and don't know of any other functions within Conky that require it being executed as root.

Location of the script: /usr/local/bin/start_conky.sh

First, run ```
gksu nautilus
``` Then create a textfile in that directory, renaming it to start_conky.sh.  Make it executable by rightclicking on the text file, then properties -> permissions -> allow executing as program Finally, add the script to your startup applications using the menu: System -> Preferences -> Startup applications -> Add

---

### Post by davegt72 on 2011-05-10
I had the same idea, but when the script runs I assume a password is required and waited for. Since it I have no way of entering said password it times out and doesn't start at all. My evidence for this theory is that well...it doesn't start at all. If sudo is taken out it runs perfectly, but doesn't display my WiFi info.

---

### Post by Dondermans on 2011-05-10
I found this on the internet:

[http://www.ducea.com/2006/06/18/linux-tips-password-usage-in-sudo-passwd-nopasswd/](http://www.ducea.com/2006/06/18/linux-tips-password-usage-in-sudo-passwd-nopasswd/)

Here's the man page on sudoers:
[http://www.manpagez.com/man/5/sudoers/](http://www.manpagez.com/man/5/sudoers/)

Particulary reaction #8 might be the solution you are looking for (replacing /bin/ps with the location of your script of course). Try to verify it with a power user before editing your /etc/sudoers file though, as the information is quite old.

---

### Post by davegt72 on 2011-05-10
> **Dondermans said:**
> I found this on the internet:

[http://www.ducea.com/2006/06/18/linux-tips-password-usage-in-sudo-passwd-nopasswd/](http://www.ducea.com/2006/06/18/linux-tips-password-usage-in-sudo-passwd-nopasswd/)

Here's the man page on sudoers:
[http://www.manpagez.com/man/5/sudoers/](http://www.manpagez.com/man/5/sudoers/)

Particulary reaction #8 might be the solution you are looking for (replacing /bin/ps with the location of your script of course). Try to verify it with a power user before editing your /etc/sudoers file though, as the information is quite old.
IT WORKED! Thank you so much.

---

### Post by Dondermans on 2011-05-10
I am glad I could help you out. :)

---

### Post by davegt72 on 2011-05-10
[SIZE=4]**SOLUTION**[/SIZE]


Script that worked:

```
#! /bin/bash
exec sudo conky -p 15
exit
```It was placed in /etc/local/conky entitled "start_conky.sh"

I had to change the default sudo password prompt setting by:
1: ```
gksu nautilus
```2: search for file "sudoers" and open it
3: change "admin ALL= (ALL) ALL" to "admin ALL=NOPASSWD: ALL" without quotes
4: save

NOTE: My script worked using this change, but I do not guarantee anyone else's will.

---

### Post by Dondermans on 2011-05-10
> **davegt72 said:**
> [SIZE=4]**SOLUTION**[/SIZE]


Script that worked:

```
#! /bin/bash
exec sudo conky -p 15
exit
```It was placed in /etc/local/conky entitled "start_conky.sh"

I had to change the default sudo password prompt setting by:
1: ```
gksu nautilus
```2: search for file "sudoers" and open it
3: change "admin ALL= (ALL) ALL" to "admin ALL=NOPASSWD: ALL" without quotes
4: save

NOTE: My script worked using this change, but I do not guarantee anyone else's will.

If I understand your solution correctly, you did create a blanket permission for all sudo commands to be executed without having to provide credentials. Thus you undermine an important security feature of Ubuntu. 

If you did so after ample consideration, I am ok with that. I just wanted to make sure you realised what you are doing here.

You might want to consider creating an exception which only affects sudo start_conky.sh.

---

### Post by davegt72 on 2011-05-10
I may not have considered these repercussions in much depth. How might I go creating an exception for only sudo start_conky.sh? I read through the second link you provided and understand the theory, but can I run something like:

```
#! /bin/bash
//change permissions to NOPASSWD
sudo conky -p 15
//change permissions to PASSWD
```

Or would add something like this to the sudoers file:

```
admin ALL=NOPASSWD: start_conky.sh
```

---


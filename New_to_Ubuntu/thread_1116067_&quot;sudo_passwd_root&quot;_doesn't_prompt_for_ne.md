---
title: "&quot;sudo passwd root&quot; doesn't prompt for new password"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by PapaJupe on 2009-04-04
[FONT="Arial Narrow"]I just installed VMWare Server 2 on my fresh install of Ubuntu 8.10. In the tutorial I was following, they recommended running the "sudo passwd root" terminal command, to change and update the root password, as that is the credential needed on your local machine to log into the VMWare Server web access panel.

I did as I was told, and the terminal is NOT prompting me for a change in the password, to "root." I try to log into VMWare with root and a blank password, all to no avail. My standard user account/credentials won't work with VMWare either,as that was specified in the installation. I did try, trust me.

Any suggestions or work arounds to updating my root credentials... with an actual propmt for a new password?? Looking forward to every and anybodies response. Thank you![/FONT]

---

### Post by rhcm123 on 2009-04-04
try running "sudo passwd nobody" to see if is a problem with the passwd program

---

### Post by kellemes on 2009-04-04
<cut>

---

### Post by PapaJupe on 2009-04-04
rhcm123: I typed in "sudo passwd nobody." It prompted me for my user password, like normal, then says "passwd: password updated successfully." I'm confuzled....

Any suggestions as to why it's behaving like this?

---

### Post by rhcm123 on 2009-04-04
> **PapaJupe said:**
> rhcm123: I typed in "sudo passwd nobody." It prompted me for my user password, like normal, then says "passwd: password updated successfully." I'm confuzled....

Any suggestions as to why it's behaving like this?

this is weird. Did you get somthing like the following output:
```
ussr@USSR-LAPTOP:~$ sudo passwd nobody
[sudo] password for ussr: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
ussr@USSR-LAPTOP:~$ 

```

---

### Post by PapaJupe on 2009-04-04
[FONT="Arial"]Not at all. Like in my last post, I received the following:[/FONT]

User@COMPNAME:~$ sudo passwd nobody
[sudo] password for User: #####
passwd: password updated successfully

[FONT="Arial"]Familiar with this behavior ? As I'm not. Looking forward to your thoughts.[/FONT]

---

### Post by rhcm123 on 2009-04-04
> **PapaJupe said:**
> [FONT="Arial"]Not at all. Like in my last post, I received the following:[/FONT]

User@COMPNAME:~$ sudo passwd nobody
[sudo] password for User: #####
passwd: password updated successfully

[FONT="Arial"]Familiar with this behavior ? As I'm not. Looking forward to your thoughts.[/FONT]

would you run the following command and post the results:
```
cat /etc/passwd | grep -i nobody
```

---

### Post by PapaJupe on 2009-04-04
nobody: x:65534:65534:nobody:/nonexistent:/bin/sh


is what I get

---

### Post by rhcm123 on 2009-04-04
> **PapaJupe said:**
> nobody: x:65534:65534:nobody:/nonexistent:/bin/sh


is what I get
then your /etc/passwd file is intact.
this might be a bug, consider telling launchpad.

try upgrading passwd as well:
```
sudo apt-get upgrade passwd
```

---

### Post by PapaJupe on 2009-04-04
rhcm123: thanks for all the help. A passwd update did nothing. Think I'll just uninstall vmware and use virtualbox, instead.

Again, thanks for the help.

---

### Post by rhcm123 on 2009-04-04
> **PapaJupe said:**
> rhcm123: thanks for all the help. A passwd update did nothing. Think I'll just uninstall vmware and use virtualbox, instead.

Again, thanks for the help.

no problem. this may be a problem with passwd. this could become serious later, but for now, if all is well, forget about it

---

### Post by llamabr on 2009-04-04
We're through the looking glass here, people.  Did anyone read the warnings on the terms of service?

We could all be banned!!!

---

### Post by rhcm123 on 2009-04-04
> **llamabr said:**
> We're through the looking glass here, people.  Did anyone read the warnings on the terms of service?

We could all be banned!!!

how? This is a legitimate problem with passwd. hes not asking for a root tutorial, he's asking for help fixing passwd

---

### Post by bodhi.zazen on 2009-04-05
I see your problem is solved.

The tutorial was obviously written by someone who does not know as much as s/he should about installing vmware on Ubuntu or sudo.

When installing vmware , watch the information on the screen. You are specifically asked to identify the name of the administrative user (default is root). Change to your login user and this problem is solved, no need to set a root password, run vmware as root, or log in as root.

Second, vmware server 2.0 uses a web interface which in my experience is quite buggy. Solution is to use vmware 1.xx or switch (as you have) to virtualbox, or if your hardware supports it, KVM.

---

### Post by rhcm123 on 2009-04-05
> **bodhi.zazen said:**
> I see your problem is solved.

Actually, no, i think his passwd command is still broken. Have you ever seen anything like this

---

### Post by bodhi.zazen on 2009-04-05
Ah, missed that.

No I have not seen this exact problem, but the fix may be :

```
sudo usermod -L root
```

Not sure as it sounds as if the OP set a blank password, and that may be throwing passwd ?

I could not re-produce the error.

perhaps post the output of:

```
sudo grep root /etc/shadow
```

---

### Post by PapaJupe on 2009-04-15
Finally, I just gave up and reinstalled Ubuntu 8.10. I dropped the option of vmware, and went to virtualbox instead. No more passwd errors... but it was really "weird" the way it suddenly all went down.

Anyway... judging from some of the other posts in this thread, I apologize for any inconveniences I might have caused with my question. :neutral: Thank you, rhcm123, for your persistence in the matter... I really appreciate that lately, on this forum.

---

### Post by rhcm123 on 2009-04-16
> **PapaJupe said:**
> Finally, I just gave up and reinstalled Ubuntu 8.10. I dropped the option of vmware, and went to virtualbox instead. No more passwd errors... but it was really "weird" the way it suddenly all went down.

Anyway... judging from some of the other posts in this thread, I apologize for any inconveniences I might have caused with my question. :neutral: Thank you, rhcm123, for your persistence in the matter... I really appreciate that lately, on this forum.

noprobs

---


---
title: "Program blocking"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by createdcreature on 2011-07-03
O.K. Let's put it into a story

I am an accountant. My children need to get into my computer to do homework, but I want to block spreadsheet programs 'Calc, Gnumeric' to protect my work content. Do you have any ideas? I run Ubuntu 10.04, not 11.04.

---

### Post by Wim Sturkenboom on 2011-07-03
Setup separate user accounts for your kids and change your password if they know it.

And change the permissions on your home directory so that only you can access them.

in a terminal
```

chmod 750 /home/yourusername

```

Try it out by logging in as one of your kids and check if you can access anything.

PS
Your kids also might have to use calc for their homework!

---

### Post by Frogs Hair on 2011-07-03
The kids account is a good idea and you can set an automatic login for them from login screen settings. Permission settings can also be made from users and groups if you prefer the GUI .

---

### Post by createdcreature on 2011-07-03
I mean a combination of inappropriate sites, program, and document blocking.

---

### Post by FatalMessenger on 2011-07-03
Okay, first, it would be a good idea to create a separate, non-administrator, account for the kids.

**Inappropriate websites**: There is plenty of filtering software out there, I have never used any of it but I believe one of the options is called dansguardian. (If anyone knows of any others, that would help)

**Document blocking**: If you create a separate account for the kids, and then from your account run the command ```
chmod 700 /home/username
``` in a terminal, they wont be able to read or write any of your files, so even if they can open your programs, they can't do any damage.

**Program blocking**: None that I know of, but like I said above, if they cant read or write to any of your files, they can't do any damage.

Hope this helps, if you have anymore questions, feel free to ask.

---

### Post by createdcreature on 2011-07-04
So there isn't anything for program blocking. The thread is marked solved now to prevent people veering off topic.

---

### Post by haqking on 2011-07-04
there are various links to running Ubuntu in kiosk mode.

I have no experience of it but i know my buddy has a kiosk login for his kids it only allows use of web browser as far as i know.

I have never really looked into it other than restricted accounts and permissions etc

---

### Post by nerdy_kid on 2011-07-04
use openDNS to filter websites.

---

### Post by createdcreature on 2011-07-04
I mean PROGRAM blocking.

---

### Post by FatalMessenger on 2011-07-04
Okay, I understand that you are an accountant and want to make it so that your kids can't mess up your work documents (understandable). You claim the only way to do this is program blocking, as we have said, there isn't really any way to block individual programs, but if you look at my previous post I explain how to make it so that they cant access ANY of your files, if it's like this they can't do any damage to the files (they cant read from, or write to, any of the files). Also, when your create a separate account for them, any thing they do to the program(s) under their account wont affect the program(s) under your account, so they can't mess anything up for you. Does that make sense?

---

### Post by createdcreature on 2011-07-04
O.K. just wondering if there is anything to block programs, but clearly there isn't

---

### Post by nerdy_kid on 2011-07-04
> **Robert Moyse said:**
> I mean PROGRAM blocking.

my apologies, you had listed "a combination of inappropriate sites, program, and document blocking.", I was trying to help out with the sites part.  There is no easy way to block access to applications afaik, a secondary user account would be the best way to go for that.

---

### Post by psrdotcom on 2011-09-15
use parental control software to block the websites and programs.:KS

---

### Post by Wim Sturkenboom on 2011-09-15
> **psrdotcom said:**
> use parental control software to block the websites and programs.:KS
Maybe you can give one or two examples of such software. Is easier for OP ;) Preferably in the repositories :lol:

---

### Post by haqking on 2011-09-15
> **Wim Sturkenboom said:**
> Maybe you can give one or two examples of such software. Is easier for OP ;) Preferably in the repositories :lol:

[http://projects.gnome.org/nanny/](http://projects.gnome.org/nanny/) it is in the repos

---

### Post by Wim Sturkenboom on 2011-09-15
On behalf of the OP, thanks :D

I don't need it, btw ;)

---

### Post by eriktheblu on 2011-09-15
Blocking programs is possible. With the multiple user accounts, create a spreadsheet users group. From there, remove all permissions to the program files for all but that user group and su.

[http://www.cyberciti.biz/faq/protect-command-by-configuring-linux-unix-group-permissions/]("http://www.cyberciti.biz/faq/protect-command-by-configuring-linux-unix-group-permissions/")

This is a fairly involved and frankly unnecessary method to accomplish the goal of protecting your files. 

Your programs can only modify the files that you have the access to modify. By simply storing the files in your home directory, by default no other user will be able to edit them.

---


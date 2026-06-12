---
title: "evolution email setup"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by misswham on 2009-06-29
I am setting up my email in evolution and i found an instructional video on how to but the server configurations are all gmail.  how do i find out what the server configurations for yahoo are?  and is that the only difference in the setup?

---

### Post by Celauran on 2009-06-29
Log into your Yahoo! account, choose Options -> Mail options, then POP & Forwarding, then View POP settings.

---

### Post by halitech on 2009-06-29
If you don't have the options for pop & Forwarding then chances are you do not have access to using pop mail access. The only accounts I've heard of are paid accounts and accounts ending with @yahoo.ca (Canada)

---

### Post by SaaTeeVaaGreen on 2009-06-29
to get the settings just log into your yahoo account as Celauran says and get the info from mail options. 

i use evolution with my yahoo account and although it works fine to fetch the mail, i cant send any emails from my yahoo account through evolution. this doesnt bother me too much as i send mail from another account which does work, but may be a problem if the same thing occurs for you...

---

### Post by misswham on 2009-07-05
Can you use Aim with evolution email?  If so how do you set it up?

---

### Post by sadaruwan12 on 2009-07-05
Yahoo! doesn't support the POP functions like gmail does thats why all the settings where from gamil. For aim check there options if they have pop forwarding enabled then that means you can use evolution with it.

---

### Post by Bandio on 2009-11-16
I have been trying to set up evolution to go through yahoo.  I could not make it work.  I set up gmail and could not make it work either.  I then change my yahoo.usa to yahoo.china.  Still could not make it work.  I then changed the encryption to TSL for receiving and SSL for Sending.  It worked the first time for sending and receiving.  But now I cannot receive any emails but I can at least send. I do not know if I am explaining this correctly. If you donot understand let me know and I will try again.;)Bandio

---

### Post by emigrant on 2009-11-16
i havent tried in yahoo. but i made it working for gmail.
if you are ok for gmail. i will write how to.

---

### Post by Skivvysam on 2010-06-27
I need to find out if Evolution supports GMail pop or only imap?
I use pop and can not get it to work as I can not set the port addresses.
 
Please help.
 
Much appreciated.

---

### Post by gandaran on 2010-06-27
> **Skivvysam said:**
> I need to find out if Evolution supports GMail pop or only imap?
I use pop and can not get it to work as I can not set the port addresses.
 
Please help.
 
Much appreciated.
both, just choose pop or imap server on evolution.
to work with pop you have to enable pop in your gmail account settings first, login to your gmail account and enable it.
then all you have to fill on the evolution to get pop mail is this
choose pop server
fill in you email username
incoming mail:  pop.gmail.com
outgoing mail:  smtp.gmail.com
and enable SSL encryption for both incoming and outgoing mail.
thats all you need, it will work.

---

### Post by plucky on 2010-06-27
> **Skivvysam said:**
> I need to find out if Evolution supports GMail pop or only imap?
I use pop and can not get it to work as I can not set the port addresses.
 
Please help.
 
Much appreciated.

To set the port address just put :993 after the pop.gmail.com address so it look like ```
pop.gmail.com:993
```

Change the port address to what is required by gmail.It is also the same procedure if you need to change the smtp port number.

Good Luck

---

### Post by gandaran on 2010-06-27
> **plucky said:**
> To set the port address just put :993 after the pop.gmail.com address so it look like ```
pop.gmail.com:993
```

Change the port address to what is required by gmail.It is also the same procedure if you need to change the smtp port number.

Good Luck

it's not necessary to enter a port number, just pop.gmail.com is the recommended option, selecting/enabling SSL encryption will automatically configure the 995 port in evolution, the 993 port I am not sure but I think is for imap mail server so if correct it wont work with pop.

---


---
title: "Forgot my password what should I do?"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by Riku Reed on 2011-06-26
Using Ubuntu 11.04, I forgot what my password was when I went to change my password I clicked by mistake on the generate password and I thought I had it copied but I don't. Is their a way I can recover that password I just forgot?

---

### Post by dFlyer on 2011-06-26
Just follow this link. Remember google is your friend:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by nzjethro on 2011-06-26
At your Grub menu, choose "Recovery Mode", then at the prompt type

```
passwd <username>
```

For example, to reset mine, I'd use

```
passwd jethro
```

EDIT: ^ dFlyer beat me to it.

---

### Post by Riku Reed on 2011-06-26
I'm going to try it out, thanks for the quick reply. :D

---

### Post by jtarin on 2011-06-26
> **Riku Reed said:**
>  Is their a way I can recover that password I just forgot?Sodium Pentothal is the ticket if the commandline doesn't work:P

---

### Post by Riku Reed on 2011-06-27
So I fixed that, everything is working now so I can login. Though I have a slight problem, when it asked for the keyring for something I typed in my newer password into the field but it said it was wrong so I tried my older password which seemed to fix that problem than it disappeared than came back saying I can't modify system etc. so I tried again put my newer password in and it worked. Weird but seems like that's all the problem their' was with that part. Anyway thanks for the help! =D

---

### Post by crispy_420 on 2011-06-27
> **jtarin said:**
> Sodium Pentothal is the ticket if the commandline doesn't work:P

Or you get the answer the questioner wants to hear...

---

### Post by ashhab2010 on 2011-06-27
that means anybody with this piece of info can change any ubuntu user's password!!!!
this is so freaky!!!!!!

---

### Post by Wim Sturkenboom on 2011-06-27
> **ashhab2010 said:**
> that means anybody with this piece of info can change any ubuntu user's password!!!!
this is so freaky!!!!!!
If physical access to a machine is possible, it's quite impossible to protect it.

---

### Post by jtarin on 2011-06-27
I think telling someone how to circumvent this in this forum is totally irresponsible. If they want the information there are other places to look. IMHO

---

### Post by nzjethro on 2011-06-27
> **jtarin said:**
> I think telling someone how to circumvent this in this forum is ... irresponsible.

I agree that it is not a good HOWTO to be widely known, however the information is very easily accesible ([ I mean, how hard is it to google?]("http://www.google.co.nz/search?sourceid=chrome&client=ubuntu&channel=cs&ie=UTF-8&q=reset+password+11.04")).

As Win says, physical acces iss required which is (usually) reasonably difficult to obtain, at least by anyone with the intention of changing your password. Also, it is possible (maybe even recommended), to set up a password on your Grub, so that the recovery mode can't be accessed, if you were worried about a security breach.

---

### Post by crispy_420 on 2011-06-27
There is always equally easy methods to do this with Windows:
[http://www.pogostick.net/~pnh/ntpasswd/](http://www.pogostick.net/~pnh/ntpasswd/)

And OSX:
[http://support.apple.com/kb/HT1274](http://support.apple.com/kb/HT1274)

---


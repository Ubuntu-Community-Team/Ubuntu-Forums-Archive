---
title: "Where is the location of my localhost?"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by penguin-of-doom on 2009-05-30
Hi,
today I have tried to go on my localhost. I went in my Browser and typed "localhost" and then there came a site with the message "It works". I find it funny, because I hadn't installed XAMPP yet. The only thing I had done is installed my System. I find it good, that I have a localhost on my PC, but how can I cange this HTML-File? Can somebody help me? Because It will be not so good if I install a second localhost on my PC when I would install XAMPP... II didn't find the file yet to change it, and I hope you can help me.

PS: Sorry for my bad english =) I'm not good at it, but I hope that you understand ma ask :D
PS2: I have installed Debian Lenny.

---

### Post by lykwydchykyn on 2009-05-30
If you haven't configured anything, it'd going to be in /var/www.  Sounds like something installed apache on your machine, maybe as a dependency (webmin used to do this).

You may not need XAMPP, unless you just prefer doing things that way.

You can run the following to see what's running on port 80:
```

sudo netstat -tunap|grep 80

```

---

### Post by penguin-of-doom on 2009-05-30
thanks for this really quick help ^^
I know now, that it is Apache which is running!
Could it be that some other people can go on my localhost if I don't protect him? And then I have to pay the Data transfer? And how can I protect the localhost?

thanks for your really good help :D

mfg

---

### Post by albinootje on 2009-05-30
> **penguin-of-doom said:**
> thanks for this really quick help ^^
I know now, that it is Apache which is running!
Could it be that some other people can go on my localhost if I don't protect him? 


Install firewall management software, see here : [http://wiki.debian.org/Firewalls](http://wiki.debian.org/Firewalls)

Or, the easiest solution :
[http://www.debian.org/doc/manuals/securing-debian-howto/ch-sec-services.en.html](http://www.debian.org/doc/manuals/securing-debian-howto/ch-sec-services.en.html) --> section 5.8 "Securing Apache".

---

### Post by lykwydchykyn on 2009-05-30
> **penguin-of-doom said:**
> thanks for this really quick help ^^
I know now, that it is Apache which is running!
Could it be that some other people can go on my localhost if I don't protect him? And then I have to pay the Data transfer? And how can I protect the localhost?

thanks for your really good help :D

mfg

Well, if you have port 80 forwarded to the machine, then yes.  I don't know what you're paying for Data transfer, but "It works!" is the only thing they'll be able to download, so it's probably not much.

If you have apache and you're not using it:
 - remove apache 
 - If you don't want to remove it, set it to only listen on 127.0.0.1 (will still come up at localhost, but will only be accessible from your own machine).
 - If you don't want to do that, install a firewall and block port 80.

Are you installing Apache/XAMPP just for development or are you planning on hosting a site on this machine?

---

### Post by penguin-of-doom on 2009-05-30
I will use the localhost to try for example my homepage on it. Or i will use it to save my files on it, and I can open them from every computer... Only for me, and not for others. My data transfer is really slow and when 10 people go on my homepage, the server will be down, so I won't do my homepage on it...
But I feel not so save when there are ports open... I will try to close them...
Paying is not the problem... I have flatrate... Could it be that somebody can get easier into my pc when I'm running for example my Homepage on it?

---

### Post by lykwydchykyn on 2009-05-30
> **penguin-of-doom said:**
> Could it be that somebody can get easier into my pc when I'm running for example my Homepage on it?

Well, IF: 
 - You are forwarding port 80 on your router, or connected directly to the internet, or on a LAN with someone who suddenly gets the urge to hack you
 - Some as-yet-unknown exploit for apache comes along which allows someone to get into your pc
 - You don't update when the patch for said exploit comes out

then, yes, it might.  But it's unlikely.

Still, leaving ports open needlessly is bad form.  

So edit /etc/apache2/ports.conf and change this line:
```

Listen 80

```
To this:
```

Listen 127.0.0.1:80

```
then restart apache:
```

sudo /etc/init.d/apache2 restart

```

That will prevent anyone but you from accessing the site.

---

### Post by penguin-of-doom on 2009-05-31
thank you! But I have scanned fot other open ports on my localhost, and I saw that there are some tcp ports open. Is this dangerous for my computer?

---

### Post by lykwydchykyn on 2009-05-31
> **penguin-of-doom said:**
> thank you! But I have scanned fot other open ports on my localhost, and I saw that there are some tcp ports open. Is this dangerous for my computer?

Well, again, it depends on the port -- or more importantly, the service listening on them.  Also depends on what sort of networks you're connecting to.

---

### Post by penguin-of-doom on 2009-06-01
What do you mean with " on what sort of networks you're connecting to"? Do you mean with this ftp, http, tcp-ports? Sorry, I do not understand

thx for your help!
regards,
penguin-of-doom

---


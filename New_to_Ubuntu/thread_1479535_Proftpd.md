---
title: "Proftpd"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by macmike on 2010-05-10
Ok I reinstalled Ubuntu Server 10.04. I then installed ProFtpd by using sudo apt-get install proftpd. It installed somewhere as standalone. I then tried to get in to the conf file with using
vi /etc/proftpd.conf and I get a blank screen with blue - down the left side at the bottom it says New File. What is wrong? Where is my Proftpd? I would like to get this where I can add my virtual hosting, 2 websites, mailman mailing list and get going. I want to get this figured out before I try and tackle putting on WordPress and Webmin.

Any help appreciated.

---

### Post by -humanaut- on 2010-05-10
try locate proftpd

---

### Post by macmike on 2010-05-10
How do I do that?

---

### Post by -humanaut- on 2010-05-10
After you login (assuming your not using a GUI) type: locate proftpd
it will find the files your looking for

---

### Post by macmike on 2010-05-10
I located them. Now how do I get out of the editor once I finish. Only way I could get out was the three finger salute. Control, alternate and delete. Not really the way I think it is suppose to be done. I still can't do anything remotely into this server. I got to figure out how to put Webmin and setup Apache to do virtual Hosting for 3 sites, 2 Websites and a mailman installation. Then what do I need to do DNS wise to get it all over. I have the three Domain names already. I know they have to all come to my public IP somehow? Big learning curve. Too bad it can be set up by someone that knows Linux better than me then put on an iso for me.

Any help with this project appreciated!

Mike

---

### Post by 3rdalbum on 2010-05-10
You don't need to use 'vi' to edit configuration files. You could use Nano instead, it's a bit more self-explanatory to use. Instead of typing:

```
vi <filename>
```

just put:

```
nano <filename>
```

---

### Post by -humanaut- on 2010-05-10
Here I'm going to direct your to a website that will literally answer all you're questions if your willing to take the time to learn [http://tldp.org](http://tldp.org) I have no idea what your level of Linux knowledge is but this site will help none the less.

---

### Post by macmike on 2010-05-11
I appreciate that. My level on Linux is low. Reminds me of my days of DOS 3.3 when I started learning DOS. I eventually learned the commands, probably forgot them by now. But, eventually learned them enough that I taught them in our Computer Division at the College where I taught at the time. I don't know if I will get that far with Linux. But, I am one that always likes a challenge and the hands on approach. Thanks for all of your patience. If I can just get my 3 sites hosted with Word Press on one and mailman on the other that will be an accomplishment for me. Gets my mind off the politics right now at work.

Mike

---

### Post by macmike on 2010-05-11
[http://tldp.org ]("http://tldp.org/")
Looks like a good site. Now where to begin. I need Virtual Hosting help how to set it up and what directory structure I need, ftp help so I can ftp files to my [www.mikealrhughes.com](www.mikealrhughes.com) site. WordPress install help so I can get my [www.wilmingtoncoc.com](www.wilmingtoncoc.com) site back up and help with mailman so I can get my [www.biblematters.net](www.biblematters.net) site moved over to my own hosting. I know I will need to figure out DNS to get this all to my pubic IP and let the computer through Virtual Hosting sort the sites. Of course I know in need something like Webmin to have a control panel. 
So that is why I need help with instructions and checklists and someone to say set you directory structure like this. I know if you answer one of these install questions wrong there goes the whole operation. One tough learning curve on this one.  Still your patience and any help appreciated. Anyone want to move to Wilmington, IL and help me for a day or two?

Mike

---


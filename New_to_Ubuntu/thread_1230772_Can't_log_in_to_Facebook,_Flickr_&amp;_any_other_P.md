---
title: "Can't log in to Facebook, Flickr &amp; any other PHP based sites."
date: 2009-08-03
forum: New to Ubuntu
---

### Post by putush on 2009-08-03
I have been using Ubuntu since 2 months now. I have Firefox 3.5.2 and Opera installed as my browsers. I have noticed, that I am unable to login to Facebook, Flickr and upload content with Flash uploader based sites like mediafire. Even basic documents created in Zoho office, I cannot store them.
It has been happening since the time I have started using the OS. Surprisingly I am able to log into Yahoo mail but not Flickr, and Facebook just allows me to view my page, I cannot do anything.
I just can't pin point where there problem is, because its being repeated on all browsers and adobe air apps on my comp, yet not by any of these service providers when I have tried to seek help.
With Firefox further, I am not able to post a thread in this forum. Although, with Opera I can.
Kindly help.
Thank you

---

### Post by stoogiebuncho on 2009-08-03
Have you disabled cookies? (in firefox: Edit > Preferences > Privacy)

Are you browsing in private mode?

---

### Post by putush on 2009-08-04
no I am not browsing in private mode. Neither are cookies disabled

---

### Post by superprash2003 on 2009-08-04
try using opendns servers - 208.67.222.222 and 208.67.220.220

---

### Post by putush on 2009-08-04
I used opendns. However, the problem is still not solved. I still cannot access the sites mentioned above.

---

### Post by stoogiebuncho on 2009-08-04
I wonder if this could be a permissions issue.  If you don't have permissions set up correctly in your settings folder, it might not let firefox save data there.

Try checking the permissions on your .mozilla folder (probably in home/username/.mozilla)

---

### Post by Chemical Imbalance on 2009-08-04
Do you have NoScript or similar add-ons installed?

---

### Post by jflaker on 2009-08-04
> **stoogiebuncho said:**
> I wonder if this could be a permissions issue.  If you don't have permissions set up correctly in your settings folder, it might not let firefox save data there.

Try checking the permissions on your .mozilla folder (probably in home/username/.mozilla)

If that is the case, then the easiest way to solve that would be to 
[LIST]
[*]export your bookmarks so you don't lose them
[*]uninstall FireFox
[*]go into your home folder and press CTL-H to unhide files and folders
[*]find the folder called .mozilla and delete it
[*]Reinstall Firefox
[*]Import your bookmarks 
[*]Try again.
[/LIST]

---

### Post by putush on 2009-08-05
No I just have adblock and element hiding enabled. The problem does not seem to be browser dependent. I have had similar problems using Opera too. Anyway, I had reinstalled firefox after deleting .mozilla, however, nothing has changed so far.

---

### Post by stoogiebuncho on 2009-08-05
Hmmm, this is an interesting one...

Have you tried connecting to those sites with a different computer (over the same internet connection)?

---

### Post by Granito_man on 2009-08-05
OK.
Did you try this:
1. On your firefox browser: edit-preferences-contents. Make sure both java and javascript are enabled.

---

### Post by putush on 2009-08-05
@ Stoogiebuncho: Yes I have connected to the same sites through a friend's laptop. They worked fine. [But he's running Windows Vista with Firefox].

@Granito-man: I have them already enabled. However, there's no change.

---

### Post by superprash2003 on 2009-08-05
2 more things you could try 
1)disable ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)
2)change MTU [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

---

### Post by putush on 2009-08-05
@superprash2003 Hi I tried out both the things you have mentioned. Problem is, its still not working. Firefox doesn't even log-in. Opera shows bad HTML request (#408 ).

---

### Post by SuaSwe on 2009-08-05
This is a slight stab in the dark but I have seen wonky ISP proxies causing this problem. Have you any set up, either in your browsers or under /etc/apt/apt.conf.d/proxy ?

Also, have you tried reinstalling Flash?

---

### Post by SuaSwe on 2009-08-05
Also, have you by any chance installed PHP or other server applications recently?

---

### Post by sikevux on 2009-08-06
I have the same issue.
The redirect after logging into this forum won't work (Looked like JavaScript)

Got Jaunty with 2.6.28-14-generic Kernel, Running both Firefox 3.0.13 and Firefox 3.5.3pre (build on the 5th of August). It's a 4 day old system.
I can use some JavaScript. E.g this small script:
[http://webdeveloper.earthweb.com/repository/javascripts/2009/05/881411/docopen.html]("http://webdeveloper.earthweb.com/repository/javascripts/2009/05/881411/docopen.html")
and this sniffer works great:
[URL="http://www.webreference.com/tools/browser/javascript.html"]
http://www.webreference.com/tools/browser/javascript.html[/URL]

Why won't some JavaScript's work?? 

Did all the stuff mentioned earlier in this thread. Post by post.
```

sikevux@elbook:~$ ls -lart | grep .mozilla
drwx------  5 sikevux sikevux       4096 2009-08-05 20:57 .mozilla

```

SAMBA is the only server software running.
And Facebook etc. worked great on the same machine 5 days ago but then it got Dells 8.04 on it. 
All the other computers (with all different kind of OSes) in my network can see Facebook etc. like it's supposed to be.

---

### Post by putush on 2009-08-06
@SuaSwe I have no PHP or other server applications. I also don't have a proxy file set up under apt.cofig.d. Reinstalled flash too.
Its still not working.

---

### Post by SuaSwe on 2009-08-06
Have you tried a LiveCD to see if you have the same problem there?

---

### Post by putush on 2009-08-06
@SuaSwe: Hi, your idea of using the LiveCD worked like a charm. Everything works as it should. However, what does this imply, do I need to reinstall my entire Ubuntu set up? Or could there be  a way to not do that?

---

### Post by sinaisix on 2009-08-06
I believe it could be with the version of Firefox you are running. Try uninstalling the 3.5.2 and install the native version that is in the repositories which i think is 3.012. If you are able to access those sites using the livecd then the problem i strongly believe is with the version of FF.

---

### Post by putush on 2009-08-06
@sinaisix I reinstalled Firefox through the repos. Running 3.5.2 and surprisingly everything is working. My problems are solved. Brilliant.

---


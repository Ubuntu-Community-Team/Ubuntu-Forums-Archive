---
title: "IEs4Linux Installation Issues on Jaunty - IE7"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by hopeididgood on 2009-07-23
I have been reading through every thread I could find on installing IE7 on ubuntu.  (While I love my firefox, unfortunately, I *need* IE7 for work. ) 

IEs4Linux seemed to be the way to go.  I don't know understand how to install the IE7 hack though. 

I'm getting stuck on the second line of these directions...

[LIST]
[*]Run IEs4Linux with this flag enabled: ./ies4linux --hack-ie7-proxy-settings
[*]After IE6 is installed, it will open. Go to Internet Options dialog and configure your proxy
[*]Close IE6 and IE7 installation should proceed
[*]Final step: comment here what you think about his hack and if it worked for you
[/LIST]
I keep getting to this line "*HACK: Configure your Proxy now and then close ie6*" in the GUI and then get completely lost.  Where is this dialog located?  (Is it Tools > Internet Options?)  And what proxy is being talked about? I can't find anything in any Internet Options tab and I have searched and searched and not been able to find a solution.  

Any advice is greatly appreciated and, alternatively, if there is a better/newer method for getting IE7 on Jaunty, please tell me.  

Thank you!

---

### Post by llamabr on 2009-07-23
Try this in the terminal:

```
chmod 755 ies4linux
./ies4linux --hack-ie7-proxy-settings
```

That's two different commands, on two different lines.

---

### Post by hopeididgood on 2009-07-23
Thank you for the suggestion. (And thank you for being specific on the lines of code -- I need directions like that!)  Unfortunately, it had exactly the same result.  The GUI starts installing IE7 and then directs me to configure my proxy & close IE6 for it to continue.  I still have no idea how to configure the proxy (or to what it is even referring to)...  I tried just closing the window, but the installation doesn't progress.  Any further suggestions?

---

### Post by philcamlin on 2009-07-23
can i see a screenshot of what screen your stuck on :popcorn:

---

### Post by hopeididgood on 2009-07-24
Yes, certainly.  (And thank you!)   

From the original directions it's my understanding I need to do something (that is, configure the proxy) in the open IE6 window, then close the window.  I am completely lost on the configuring proxy part and just closing IE6 fails to advance the installation.  

[IMG]http://i15.photobucket.com/albums/a374/Stellastars/Screenshot-InternetExplorersforLinu.png[/IMG]

---

### Post by msayag on 2009-08-13
The problem is that IE6 never really closed.
After closing IE6 I opened the system monitor and found a process called IEXPLORER and is in status Zombie.
Kill it and the script will proceed

---

### Post by alexlafreniere on 2009-08-13
Are you installing IE7 on your laptop at work, where you most likely are behind a proxy? I had the same problem with IEs4Linux, but all I had to do was edit a configuration file that allowed the installer to fetch the files it needed from behind my work's proxy.

---


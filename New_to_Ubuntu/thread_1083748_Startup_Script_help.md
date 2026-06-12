---
title: "Startup Script help"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by championboxes on 2009-03-01
I need help making a bash script that on startup will run conky and vino-server (/usr/lib/vino/vino-server)
so far all I got is ```
#!/bin/bash
sleep 20 && conky
```

---

### Post by ajgreeny on 2009-03-01
You need
```
#!/bin/sh
sleep 20; conky && /usr/lib/vino/vino-server
```I don't really know conky, but if the executable file for it is in a normal system path (eg /usr/bin) you will not need the full pathway to it, just **conky**.

---

### Post by championboxes on 2009-03-01
When I want to run conky all i have to do is type conky in the terminal but to get run vino-server I have to cd to the location of the file then type ./vino-server should that affect the script? and thanks for your help

---

### Post by ajgreeny on 2009-03-01
There should be no problem with conky if it runs from the command ```
conky
``` You need the full pathway for vino-server because it is not in one of the default pathway folders of the system.

Can you look to see if the file vino-server is an executable shell script or file with ```
ls -l /usr/lib/vino/vino-server
```If so, and there are some "x"s showing in the permissions, you can just use the full pathway, as I said and it should work, if not, and I suspect that will be the case, it will mean that you either need to use the prefix  ./ before the file will execute, or you need to make it executable.

---

### Post by thtrgremlin on 2009-03-01
just a possible suggestion, if you just want thise programs to start at boot, you can add a line to your startup using the session manager.

System -> Preferences -> Sessions
I'd also note that ```
sleep 20; conky && /usr/lib/vino/vino-server
```
will wait 20 seconds, then run conky, then if conky exits successfully, then will start vino-server. If you want them to both run, then you need to use a single '&' which will start conky in the background, and then start vino-server. I'd further recommend backgrounding vino-server unless you want the script to stay running doing nothing waiting for vino-server to exit. It could also be prudent to create a log file for the scripts output, otherwise you can get undefined results. So all that together, consider:
```
#!/bin/bash
sleep 20;
conky 2>&1>>/var/log/foo.log &
/usr/lib/vino/vino-server 2>&1>>/var/log/foo.log &
exit 0
```

And, just cause I got to give a shout out, the bash man page is AWSOME, albeit long.

Just curious, why the sleep 20s?

---

### Post by championboxes on 2009-03-02
> ls -l /usr/lib/vino/vino-server With the ls command I got -rwxr-xr-x 1 root root 178416

> #!/bin/bash
sleep 20;
conky 2>&1>>/var/log/foo.log &
/usr/lib/vino/vino-server 2>&1>>/var/log/foo.log &
exit 0 I used this but i couldnt get the log thing to work but the script is working now on startup thanks for all the help guys and for the sleep 20; I guess I dont have a really good reason to do that other than thats what I have on my laptop because of beryl should that be the only reason I should use sleep? 

One more thing how do I mark this thread as solved? I thought there was suppost to be a drop down menu but I cant find it anywhere?

---

### Post by thtrgremlin on 2009-03-02
Go back to your original post, click 'edit' in the bottom left corner. click 'advanced' and then edit the thread name and just prepend it with the text '[SOLVED]'

I wish a lot more people would do that, then it would be easier to find threads where people were looking for help without having to read through everythig first. I wish there was some button you could click to take care of thatreally easily, or admins would just go through and change the names as they came by them.

I LOVE the way launchpad does it, but launchpad has its own issues, and I don't think the structure would be as great for how wild the conversations sometimes get over here  :)

---

### Post by ajgreeny on 2009-03-02
>  				 				**Re: Startup Script help** 			
 			 			 		   		 		 		Go back to your original post, click 'edit' in the bottom left corner. click 'advanced' and then edit the thread name and just prepend it with the text '[SOLVED]'

I wish a lot more people would do that, then it would be easier to find threads where people were looking for help without having to read through everythig first. I wish there was some button you could click to take care of thatreally easily, or admins would just go through and change the names as they came by them.

I LOVE the way launchpad does it, but launchpad has its own issues, and I don't think the structure would be as great for how wild the conversations sometimes get over here :smile:
 		                   		  		  		 		 			 				__________________
				If all else fails, read the documentation. There's nothing sissy about a MAN page. 			
Until quite recently, though I can't remember when, I think there was a button to allow both "Solved" and "Thanks" to be added to posts.  At the moment these are both non-active, but they are supposed to be returning.

---

### Post by thtrgremlin on 2009-03-02
I really look forward to seeing that in the near future. It is glaringly obvious they are just missing considering the way so many of the other ubuntu interactive pages operate. I know they are independent, but of places one could grab advice from, and for the purpose this page serves, and further so much of the "tech support" being volunteers (almost everyone?), it would be a big help.

Also, when searching for answers, to often I am looking for an answer and get results of simply many unanswered posts. Not very pragmatic, is it?

---


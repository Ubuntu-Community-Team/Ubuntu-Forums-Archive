---
title: "synaptic manager is not working with following error"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by GK Srinivasa on 2010-04-19
please rectify this problem,synaptic manager is not working with following error.

E: type-- 2010-04-06 is not known on line 1 in  source list/etc/apt/sources.list.d/midibuntu.list
the list of sources could not be read
goto the repository dilog to correct the problem
E: cache>open() failed please report

---

### Post by Drenriza on 2010-04-19
can you plaste the output of

```
cat /etc/apt/sources.list
```

here?

---

### Post by GK Srinivasa on 2010-04-19
bash:cat/etc/sources.list:no such file or directory

---

### Post by wilee-nilee on 2010-04-19
> **GK Srinivasa said:**
> bash:cat/etc/sources.list:no such file or directory

Look closer at the code, just copy and paste it.

---

### Post by WinterRain on 2010-04-19
> **GK Srinivasa said:**
> please rectify this problem,synaptic manager is not working with following error.

E: type-- 2010-04-06 is not known on line 1 in  source list/etc/apt/sources.list.d/**midibuntu.list**
the list of sources could not be read
goto the repository dilog to correct the problem
E: cache>open() failed please report

The medibuntu server is down right now. Be patient and it will come back. There is no real error.

---

### Post by Drenriza on 2010-04-19
If the server is just down, the "error" will disapear by itself. Leaving this thread.

:):KS

---

### Post by GK Srinivasa on 2010-04-19
Resonse for above command is no such file or dirctory ,please

---

### Post by GK Srinivasa on 2010-04-19
it has been from one week

---

### Post by GK Srinivasa on 2010-04-19
**synaptic manager is not working with following error** 			
 			 			 		   		 		 		please rectify this problem,synaptic manager is not working with following error.

E: type-- 2010-04-06 is not known on line 1 in  source list/etc/apt/sources.list.d/midibuntu.list
the list of sources could not be read
goto the repository dilog to correct the problem
E: cache>open() failed please report:guitar:

---

### Post by wilee-nilee on 2010-04-19
> **GK Srinivasa said:**
> **synaptic manager is not working with following error** 			
 			 			 		   		 		 		please rectify this problem,synaptic manager is not working with following error.

E: type-- 2010-04-06 is not known on line 1 in  source list/etc/apt/sources.list.d/midibuntu.list
the list of sources could not be read
goto the repository dilog to correct the problem
E: cache>open() failed please report:guitar:

So you might inspite of the server being down post the command I notice a misspelling of medibuntu as midibuntu, did you type this?

---

### Post by GK Srinivasa on 2010-04-19
yes

---

### Post by GK Srinivasa on 2010-04-19
E: type-- 2010-04-06 is not known on line 1 in  source list/etc/apt/sources.list.d/midibuntu.list
the list of sources could not be read
goto the repository dilog to correct the problem
E: cache>open() failed please report

this is typed.

:guitar:

---

### Post by mick222 on 2010-04-19
> **GK Srinivasa said:**
> E: type-- 2010-04-06 is not known on line 1 in  source list/etc/apt/sources.list.d/midibuntu.list
the list of sources could not be read
goto the repository dilog to correct the problem
E: cache>open() failed please report

this is typed.

:guitar:
 you need to edit your sources open system -> administration -> Software sources and on the other software tab uncheck anything with midibuntu in it .
close and try to update if that works go back to the sources and edit the lines you unchecked to mediabuntu .Also you keep posting new threads on this subject please dont do that it just confuses everyone .Including yourself.

---

### Post by lisati on 2010-04-19
> **GK Srinivasa said:**
> please rectify this problem,synaptic manager is not working with following error.

E: type-- 2010-04-06 is not known on line 1 in  source list/etc/apt/sources.list.d/midibuntu.list
the list of sources could not be read
goto the repository dilog to correct the problem
E: cache>open() failed please report

Please do not start multiple threads or hijack other people's threads.

[LIST=1]
[*]What you have typed is incorrect. "midibuntu" should be "medibuntu"
[*]As requested, please reply with the output from the following command: ```
cat /etc/apt/sources.list
```
[/LIST]

---

### Post by lisati on 2010-04-19
It seems that other people are having trouble with the medibuntu repostiries as well. Once you have fixed your spelling mistake, have a look here: [http://ubuntuforums.org/showthread.php?t=1457340](http://ubuntuforums.org/showthread.php?t=1457340)

---

### Post by 3rdalbum on 2010-04-19
***_The spelling mistake doesn't matter._*** What matters is that the contents of the file are completely wrong.

Run this command to remove the file that is causing the problem:

```
sudo rm /etc/apt/sources.list.d/midibuntu.list
```

And try the Medibuntu repository HOWTO again, and this time just copy and paste it into the terminal rather than type it out.

---

### Post by zeroseven0183 on 2010-04-21
I found this website which might help you, guys.
[WebUp8: Medibuntu Repository is Down - What To Do?]("http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html")

You need to look for a mirror and modify your sources.list

---

### Post by polly1 on 2010-04-21
Hi

I think this solution may be easier than by amending the 
/etc/apt/sources.list.

Please see this thread [http://ubuntuforums.org/showthread.php?t=1458747](http://ubuntuforums.org/showthread.php?t=1458747)

Start Synaptic Manager, then Settings,and then Repositories. Take the action per Morius1`s post and your Update Manager problem should be solved.

It just worked for me on Karmic and (beta) Lucy and will presumably do so on previous Ubuntu s. 

Cheers

:guitar:

---

### Post by zeroseven0183 on 2010-04-21
> **polly1 said:**
> Hi

I think this solution may be easier than by amending the 
/etc/apt/sources.list.

Please see this thread [http://ubuntuforums.org/showthread.php?t=1458747](http://ubuntuforums.org/showthread.php?t=1458747)

Start Synaptic Manager, then Settings,and then Repositories. Take the action per Morius1`s post and your Update Manager problem should be solved.

It just worked for me on Karmic and (beta) Lucy and will presumably do so on previous Ubuntu s. 

Cheers

:guitar:

I see that we are on the same page. The mirrors suggested in your link are the same as in the link I posted. Good good good! :)

---


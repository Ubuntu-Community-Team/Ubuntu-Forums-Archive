---
title: "How can I run MS Office 2007 on ubuntu 8.10"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by izzyz on 2009-04-10
Hi I would completely abandon Windows which I am currently using just for MS Office - I have to for my college projects. Is there a way I could use Office on ubuntu?

I heard of Wine, tried to install it, and then install Ms Office 2007 on it - using tips from this forum (although they were for previous versions of ubuntu), but I failed numerous times. 

Could anyone guide me step by step how do I install it?

Many thanks

---

### Post by kdreimiller on 2009-04-10
i use wine 1.1.15 and run office with almost zero problems.  i think winehq has some tips for installing and running it really well.  i remember having to enable a few things to make it run great, but nonetheless i had no problems installing from the office 07 install CD

---

### Post by Hospadar on 2009-04-10
If you have difficulty running it in wine, consider using a virtual machine like virtualbox, it's very easy to set up and will run windows programs flawlessly, albeit with a larger performance footprint than wine (although depending on your system this may or may not be a problem)

---

### Post by germanix on 2009-04-10
The simplest way around this problem is to do all your work with Open Office and then save that work as Microsoft Office files if you need to. With open office you can also open all microsoft office files, and any way everything you can do with MS office you can also do with Open office. Besides open office is frre and included in Ubuntu.
I have never used wine so if my advice is not that what you want I am sure someone else will respond to your question

---

### Post by kdreimiller on 2009-04-10
i had to install office 2007 because i needed it for school as well.  some of the stuff i would do in open office didnt translate right when i would open it on the computers at school.  and since the course i was taking was a ms office course (dont ask!) i was kind of railroaded into buying and installing it

---

### Post by djbushido on 2009-04-10
If you absolutely have to have MS Office, virtualbox is your best bet. you can mount a usb drive and save out, send to email, or some other method to get files out of the virtual machine.

---

### Post by Therion on 2009-04-10
> **kdreimiller said:**
> i had to install office 2007 because i needed it for school as well.  some of the stuff i would do in open office didnt translate right when i would open it on the computers at school.  and since the course i was taking was a ms office course (dont ask!) i was kind of railroaded into buying and installing it
Well if I was going to take a course in MS Office, I would fully expect to have to use MS Office.  

I'd suggest you go the Virtual Box route for this, personally.

---

### Post by theozzlives on 2009-04-10
> **germanix said:**
> The simplest way around this problem is to do all your work with Open Office and then save that work as Microsoft Office files if you need to. With open office you can also open all microsoft office files, and any way everything you can do with MS office you can also do with Open office. Besides open office is frre and included in Ubuntu.
I have never used wine so if my advice is not that what you want I am sure someone else will respond to your question

Not true you can't handle MS Publisher files with Open Office.

---

### Post by izzyz on 2009-04-10
I appreciate your suggestions, could you guide me through that please? I dont want to sound stupid but I am new to linux and have no idea what that virtual box is.

Thanks

---

### Post by kdreimiller on 2009-04-10
sadly the course is called "intro to computer systems." the only "system" they introduce you to is MS office.  they dont even go over any MS operating systems. so the inaccurately named course is all about MS 07 basics. unfortuantely it's a required course.

but wine works great for me, no need for virtual box and the class ends in a few weeks anyways.

---

### Post by Therion on 2009-04-10
> **izzyz said:**
> I appreciate your suggestions, could you guide me through that please? I dont want to sound stupid but I am new to linux and have no idea what that virtual box is.
Happy to help, but... 

Going the the Virtual Box route *requires* a Windows install CD.  Not a factory "Restore" CD, not an upgrade CD... A full-blown Windows installation CD.  

Do you have one?  Because if you don't this is a moot point.

---

### Post by Dileeshvar on 2009-04-10
the best way is to use open office 
you could save it in windows format 
so where is the need for MS office ???

and it is lot better than MS office 

:guitar:

---

### Post by cyberphrog on 2009-04-10
> **kdreimiller said:**
> sadly the course is called "intro to computer systems." the only "system" they introduce you to is MS office.  they dont even go over any MS operating systems. so the inaccurately named course is all about MS 07 basics. unfortuantely it's a required course.

but wine works great for me, no need for virtual box and the class ends in a few weeks anyways.

Sounds like a completely useless course.  I'd recommend that you withdraw from it and take a more useful (and interesting) course.

---

### Post by MattBD on 2009-04-10
[Oxygen Office]("http://sourceforge.net/projects/ooop") is based on OpenOffice but apparently works more like MS Office 2007, so that might be worth a try. The site only seems to offer an RPM so you'd need to use alien to convert the rpm into a .deb file for Ubuntu.

---

### Post by izzyz on 2009-04-10
I do need MS Office 2007, so OpenOffice is unfortunately not an option. And no I dont have Windows CD either! 

I suppose I will have to use wine instead...

I followed the thread how to :

[http://ubuntuforums.org/showthread.php?t=922963&highlight=ms+office+2007](http://ubuntuforums.org/showthread.php?t=922963&highlight=ms+office+2007)

but the command winecfg failed, here's what it said:

izzy@izzy-desktop:~$ winecfg
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\services.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\services.exe" failed, status c0000135
err:wineboot:start_services_process Unexpected termination of services.exe - exit code -1073741515
err:module:import_dll Library rpcrt4.dll (which is needed by L"C:\\windows\\system32\\ole32.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\winecfg.exe" failed, status c0000135
izzy@izzy-desktop:~$ 


If anyone could assist that would be great

thanks

---

### Post by Therion on 2009-04-10
Ugh.  I was afraid of that.  I don't mind telling you I'm NOT a big fan of Wine, but sometimes you gotta do what you gotta do.  

See the following tutorial for installing MSO via Wine in Ubuntu...  

[http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/](http://samanathon.com/how-to-install-microsoft-office-2007-in-ubuntu-804/)

---

### Post by mdsmedia on 2009-04-10
I only have a Windows Restore CD, but I found a How To to create a system CD, yesterday. I'm in the process of installing Windows in VirtualBox at the moment. It's taken hours (I only have 512MB of RAM) so I don't know if it will even be successful.

---

### Post by kdreimiller on 2009-04-10
> **cyberphrog said:**
> Sounds like a completely useless course.  I'd recommend that you withdraw from it and take a more useful (and interesting) course.

not completely useless, i am learning office pretty well.  and it would be silly to withdraw - its an easy A, and like i said, its required for the program im in.

tho i have thought about giving the dean a few choice words about the course, well at the very least, the course description.

---

### Post by TheNosh on 2009-04-10
> **kdreimiller said:**
> i am learning office pretty well..

your learning M$ office pretty well. thats how they maintain their monopolly, they make their programs the only ones people are taught

open office, star office, and (my personal favorite for now) IBM lotus symphony are all at least as good as M$ office

that being said, i'm pretty sure it can be run in wine, but if not you can deffinately run it through crossover (but that costs moey)

---

### Post by izzyz on 2009-04-11
Guys your posts are completely unrelated to my problem! Im not interested in Ms Office courses. All I am asking for is help or step by step guide on how to install it on ubuntu 8.10 using wine, since Im completely new to linux. Your links to other guides use ubuntu 8.04, maybe that is why Im having problems?
How do I delete all previous files wine related, so I can start fresh install? that  may be another reason why Im having problems.

Thanks

---

### Post by woodenbrick on 2009-04-11
As long as there is no other wine related software that you have installed and want to keep, you can just delete the .wine folder in your home directory to start afresh.

---

### Post by albinootje on 2009-04-11
> **izzyz said:**
> Is there a way I could use Office on ubuntu?


I suggest to take a look at CrossOverLinux.
The MS-Office 2007 gets a "bronze" value in the CrossOverLinux database, which might be good enough for what you need MS-Office for.

[http://www.codeweavers.com/compatibility/browse/name/?letter=m;](http://www.codeweavers.com/compatibility/browse/name/?letter=m;)

---

### Post by RetchingRabbit on 2009-04-11
> **theozzlives said:**
> Not true you can't handle MS Publisher files with Open Office.
Right, and I don't believe you can run publisher in wine or other emulation environments, either.

---

### Post by raymondh on 2009-04-11
> **izzyz said:**
> Guys your posts are completely unrelated to my problem! Im not interested in Ms Office courses. All I am asking for is help or step by step guide on how to install it on ubuntu 8.10 using wine, since Im completely new to linux. Your links to other guides use ubuntu 8.04, maybe that is why Im having problems?
How do I delete all previous files wine related, so I can start fresh install? that  may be another reason why Im having problems.

Thanks

Have a read at this thread.  OP there seems to have installed it as well as have/make some fixes.

[http://ubuntuforums.org/showthread.php?t=922963&highlight=install+ms+office](http://ubuntuforums.org/showthread.php?t=922963&highlight=install+ms+office)

Hope this helps.

Enjoy the learning,

Raymond

---


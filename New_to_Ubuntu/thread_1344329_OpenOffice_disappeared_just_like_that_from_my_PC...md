---
title: "OpenOffice disappeared just like that from my PC....."
date: 2009-12-02
forum: New to Ubuntu
---

### Post by suomalainen on 2009-12-02
Ubunteros,

This afternoon I installed an additional language pack into Ubuntu. This was done in addition to English.

I rebooted my PC to see if I could logon using this new language. IT worked.

When I went to:

Applications ---> Office

Only Evolution Mail and Calendar appeared. Everything else that was dealing with OpenOffice like word processor, spreadsheet etc... Just disappeared.

I rebooted then logged on in English and same story........


I'm using 8.04LTS. So does this version have any protection in place so that I can undo what was done?

Or what should I do to get everything restored.....????

Actually, I don't even know what has happened....

Thanks for your help on this all......

---

### Post by wojox on 2009-12-02
Did you double check the Main Menu app to see if they appear in their?

---

### Post by suomalainen on 2009-12-02
> Did you double check the Main Menu app to see if they appear in their?

Where is the Main Menu App???? I don't understand. Sorry.

---

### Post by Sef on 2009-12-02
It is under Preferences.

---

### Post by BandD on 2009-12-02
Can you open openoffice by pressing alt+F2 and then typing openoffice.org?

---

### Post by wojox on 2009-12-02
Go to the Applications Menu and right click and choose Edit Menus then select Office from the left column. See if their checked in the right column.

---

### Post by frank002 on 2009-12-02
Go to System>Preferences>Main Menu. Click on the left panel where it says Office and see if your Open Office apps are still there.

---

### Post by suomalainen on 2009-12-02
Thanks for the response everyone!!

As per:

> It is under Preferences.

I still don't understand you. Where do you want me to go to see this. "Preferences"???????

I ran the openoffice.org command and the attached pic show the error message I received.

---

### Post by wojox on 2009-12-02
Click on System > Preferences > Main Menu

---

### Post by suomalainen on 2009-12-02
Thank You everyone for the help thus far.

Based on the current info I received it looks as if the files have disappeared?

I attached a screenshot of what I found.

Thank you again.

---

### Post by wojox on 2009-12-02
So if you check mark OpenOffice and close the menu and go to Applications > Office > OpenOffice what does it do. This is rather strange from a language pack install.

---

### Post by suomalainen on 2009-12-02
Just to clarify:

> So if you check mark OpenOffice and close the menu and go to Applications > Office > OpenOffice what does it do

What you are marking is OpenOffice.org. Once this is done and you go to:

Applications > Office > OpenOffice.org

And click on it NOTHING HAPPENS......

---

### Post by wojox on 2009-12-02
It has to be their. Go to Places > Search for Files. Type in OpenOffice and change the Look in folder to File System

---

### Post by suomalainen on 2009-12-02
wojox,

Thanks for the advice and guidance. I did what you told me to do and found alot!

Hopefully the attached txt file explains alot.

Thanks again.

---

### Post by suomalainen on 2009-12-02
By the way, did I find the files I need to get these OpenOffice programs to launch?

Thanks

---

### Post by BandD on 2009-12-02
What happens when you run:

```
openoffice.org
``` 

in a terminal (Applications--> Accessories--> Terminal)?

I couldn't view the .txt files you attached previously btw.  Not sure why, but gedit didn't like them.

*Edit* Nevermind about the files, I had to actually download them.  Once I downloaded them, gedit had no problem with them.  It seems that all the files are there.  So it should run.

---

### Post by suomalainen on 2009-12-02
Hi BandD,

Running the command I got


paul@paul-desktop:~$ openoffice.org
bash: openoffice.org: command not found
paul@paul-desktop:~$ 


I noticed the same as you regarding the txt files. But when I saved them to the desktop and then double clicked they opened just fine. Wierd....


Thanks again.

P.S. This command was already referenced on page one.

---

### Post by suomalainen on 2009-12-02
> *Edit* Nevermind about the files, I had to actually download them. Once I downloaded them, gedit had no problem with them. It seems that all the files are there. So it should run.

It's great to hear that you believe all the files are there. If this is the case then I need to figure out how to link everything back together again...

But I don't know how to do this. Do you?

---

### Post by BandD on 2009-12-02
It seems that the alias somehow got messed up.  It honestly might be easier to try and reinstall the openoffice.org meta package via Synaptic (System --> Administration --> Synaptic).  

I really don't know how a language pack would have messed things up so badly...it's strange.

---

### Post by wojox on 2009-12-02
I was able to open you files with OpenOffice. How ironic. I agree with BandD. I did not see any refrence to calc, draw, writer, math....

---

### Post by BandD on 2009-12-02
I hate to leave you without helping too much more.  But I have to go.  I'll check back in the morning, but most likely it will be about 24hrs before I'm able to offer any other advice.

Good luck.

---

### Post by suomalainen on 2009-12-02
Thanks all!

I don't know why but I'm unable to install OpenOffice now.

Attached are the pics in order 0,1,2  which shows that I'm unable to complete the install.

Any ideas?

---

### Post by suomalainen on 2009-12-03
UPDATE,

I used Synaptic to uninstall everything with the name "OpenOffice". Then I reinstalled. Now I got OpenOffice. But this is version 2.4 The previous version I had was 3.0. Perhaps that caused a conflict of some sort????

Don't know for sure....

Any other thoughts out there?

---

### Post by Aflack on 2009-12-03
try uninstall with synaptic then installing from the openoffice site?

---

### Post by suomalainen on 2009-12-03
AGAIN :o Why would I want to do that?

---

### Post by Aflack on 2009-12-03
> **suomalainen said:**
> AGAIN :o Why would I want to do that?

so you can use open office???

---

### Post by longtom on 2009-12-03
If OO 2.4 is fine for you, you don't need to do anything.

If you want or need 3.0 for some reason you can follow this route:

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

Good Luck

---

### Post by wilee-nilee on 2009-12-03
> **longtom said:**
> If OO 2.4 is fine for you, you don't need to do anything.

If you want or need 3.0 for some reason you can follow this route:

[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

Good Luck

Gdebi is the easiest way to install this down load just double click on the download or right click and choose gdebi.

OP if you decide to do a download directly from Ope3n Office make sure you have removed every OO 2.4 file along with the OO file on home.

---

### Post by suomalainen on 2009-12-03
Thanks for all the help everyone!!! Especially the How-to install link...

10.04LTS isn't that far away from launch so maybe its better to just wait?

I guess there will be an even newer version of OpenOffice at that time as well????

Thanks again.

---


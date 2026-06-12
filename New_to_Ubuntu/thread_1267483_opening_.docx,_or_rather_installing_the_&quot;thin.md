---
title: "opening .docx, or rather installing the &quot;thingy&quot;"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by rahrahmah on 2009-09-15
So I want to install the little thingy that lets me open .docx files. I have it all downloaded onto the desktop and I opened the terminal and I ran the command:

sudo dpkg -i odf-converter_1.0.0-2~getdeb1_i386.deb

because that's what the website told me to. But I get an error. What am I doing wrong?

---

### Post by markusf21 on 2009-09-15
you can just double click .deb files to install

---

### Post by sandyd on 2009-09-15
> **rahrahmah said:**
> So I want to install the little thingy that lets me open .docx files. I have it all downloaded onto the desktop and I opened the terminal and I ran the command:

sudo dpkg -i odf-converter_1.0.0-2~getdeb1_i386.deb

because that's what the website told me to. But I get an error. What am I doing wrong?

run
```

sudo apt-get -f install
```

---

### Post by rahrahmah on 2009-09-15
When I double click it I also get an error:

[/home/aurora/Desktop/AVSVideoConverter.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/aurora/Desktop/AVSVideoConverter.exe or
          /home/aurora/Desktop/AVSVideoConverter.exe.zip, and cannot find /home/aurora/Desktop/AVSVideoConverter.exe.ZIP, period.

---

### Post by Bölvaður on 2009-09-15
If this converter is old then installing open office 3 might work.

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

This how-to uses 8.10 which is named intrepid, you will need to change *intrepid* to *jaunty* if you are on 9.04

if you are on 8.04 the long term service release then change it to *hardy*

But then again, if you are on 9.04 then you already have a relatively new version of open office that should do what you want.


Alternatively you can ask the person to save the file as .odf (or something like that) which should be easier to handle. That is if that person has updated his/her office suit.

---

### Post by Bölvaður on 2009-09-15
> **rahrahmah said:**
> AVSVideoConverter.exe

this is the wrong file, click on the  odf-converter_1.0.0-2.deb

---

### Post by balachandarlinks on 2009-09-15
Yes..just upgrading your open office to 3.0 will open .docx format for ou.

---

### Post by rahrahmah on 2009-09-15
If it is the wrong file, then do you know where I could download the right one? This is the file that the website "ubuntu geeks" told me to get. I'm on 9.04 and already have open office 3, and it definitely does not open .docx

---

### Post by scrooge_74 on 2009-09-15
Open Office 3 takes care of those damn propietary formats ;)

---

### Post by rahrahmah on 2009-09-15
No, really, I HAVE open office 3 already, and the newest ubuntu. It really really doesn't open those files.

---

### Post by scrooge_74 on 2009-09-15
Weird, I remember opening one of those docx documents the other day, I doubt Debian version of OO has trick up its sleeve

---

### Post by Excedio on 2009-09-15
I just tested it...opened like a charm. I use OOo 3.1.

---

### Post by rahrahmah on 2009-09-16
Well, I just tested it, and it still doesn't work for me. Please, I need this for school

---

### Post by Excedio on 2009-09-16
> **rahrahmah said:**
> Well, I just tested it, and it still doesn't work for me. Please, I need this for school

If your file is not private, would you be willing to send me a copy of the docx file to see if it will open in my computer? If you are, go ahead and send me a PM.

---

### Post by 3rdalbum on 2009-09-16
> **rahrahmah said:**
> So I want to install the little thingy that lets me open .docx files. I have it all downloaded onto the desktop and I opened the terminal and I ran the command:

sudo dpkg -i odf-converter_1.0.0-2~getdeb1_i386.deb

because that's what the website told me to. But I get an error. What am I doing wrong?

You're not telling us what error message you're getting; that's what you're doing wrong :-P

---

### Post by mike555 on 2009-09-16
perhaps the file your trying to open is bad ... you could download a test .docx from here (at the top of the page is downloadable file) ...    [http://examples.maartenballiauw.be/WordVisualizer/Documents/test2.docx](http://examples.maartenballiauw.be/WordVisualizer/Documents/test2.docx)

---

### Post by rahrahmah on 2009-09-16
/tmp/test2.docx could not be opened, because the associated helper application does not exist. Change the association in your preferences.

Nope. I can't open it. And I'm afraid I cant send you the .docx because it's on my college's private system. 

And as for you,** 3rdalbum **all it said was that "there was an error". That's all it said in the terminal. When I double clicked it I wrote out the error it gave me there in full. I don't know what else you want from me, but I can tell you I really don't appreciate that attitude. This is important, it's for school. I don't know how I'm going to participate in this course if I can't read and critique most of the things my peers are submitting. So go be a jerk in another thread. ":P"

---

### Post by oldos2er on 2009-09-16
> **rahrahmah said:**
> /tmp/test2.docx could not be opened, because the associated helper application does not exist. Change the association in your preferences.


  Did you change the association? Right-click on the *docx file, Properties, Open with....

---

### Post by roger_1960 on 2009-09-16
Hi

If I just click on that "test2" file I get the same error.  But, if I save it and then right click on it and select "open with openoffice..." it works!

---

### Post by ashwinhgtx on 2009-09-16
Right click, go to properties, and change the open with dialogue to OpenOffice.

Then any double click should open the file with OpenOffice.

---

### Post by TheStroj on 2009-09-16
Open Office 3.1 can open it, so update your current version of Open Office. If you still can't open it, then the file is probably corrupted.

Copy all this to terminal and press enter. It will install openoffice 3.1 by itself!

```

echo -e 'echo "#PPA openoffice-pkgs
deb http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/ppa.list

gpg --keyserver keyserver.ubuntu.com --recv 247d1cff
gpg --export --armor 247d1cff | sudo apt-key add -

sudo apt-get update

sudo aptitude -y safe-upgrade
sudo aptitude -y dist-upgrade
' > ./oooupgrade.sh
sudo sh ./oooupgrade.sh && rm ./oooupgrade.sh

```

---

### Post by egalvan on 2009-09-16
> **rahrahmah said:**
> [COLOR="Red"]/tmp[/COLOR]/test2.docx could not be opened, because the associated helper application does not exist. Change the association in your preferences.

It's not usual to have user files in [COLOR="Red"]/tmp[/COLOR].
This is a temporary directory, not normally used to store files that will be worked on by users.

> 
And I'm afraid I cant send you the .docx because it's on my college's private system. 

Do you mean that the system is private, and you are not allowed to send the file?

Or that the file is private,  and you are not allowed to send the file?

Or that the file has private content that should not be seen by un-authorized users?

> And as for you,** 3rdalbum **all it said was that "there was an error". That's all it said in the terminal. When I double clicked it I wrote out the error it gave me there in full.
I don't know what else you want from me, but I can tell you I really don't appreciate that attitude.
This is important, it's for school. I don't know how I'm going to participate in this course if I can't read and critique most of the things my peers are submitting. So go be a jerk in another thread. ":P"

And as for ** 3rdalbum **, well I had the exact same thought as him... you were not giving us enough information to make truly informed guesses as to your problem.

Granted, it may be important to ***you***, but to others, it has no significance beyond helping others.

3rdalbum, along with everyone else that has given help on this forum,
is a **volunteer**.
And he's been at it for quite some time.

He was not being a **jerk**. You asked a question, and didn't give much in the way of information.

And he answered you the way most of us would have...

With a humorous statement that you had not given enough information.

Eric Steven Raymond (yes, THAT Eric Raymond) has some good insights into this. Give it a good read, it may help you here, and beyond.

[http://catb.org/~esr/faqs/smart-questions.html](http://catb.org/~esr/faqs/smart-questions.html)


And in closing...
learning how to solve your problems is one of the things that a good education is supposed to teach you.

---

### Post by SunnyRabbiera on 2009-09-16
> **rahrahmah said:**
> No, really, I HAVE open office 3 already, and the newest ubuntu. It really really doesn't open those files.

Odd, .docx wo0rks fine here.

---

### Post by rahrahmah on 2009-09-16
Well, the update worked properly (thankyou! this is the first time I've been able to make the terminal do anything other than frustrate and depress me) but I'm still having the same problem. I tried saving, and looking at the properties, but it is already set to open with open office.

I can tell you I know the file isn't corrupt because I opened it just today on the Windows machines at my school.

And my I restate the point that I DID LIST MY ERROR MESSAGES. The terminal only said "there was an error". I suppose I could append "processing your request" but I didn't think that was relevant. You may continue to cast aspersions on my character, level of education, and educational institute for that fact if you like. I didn't get a proper error message until I tried double clicking the file I had downloaded, and I LISTED THE WHOLE THING. To come into a thread that's all the way down the page and respond to the first post without reading anything else seems far more ignorant than anything I did. And as for humour, I didn't find it funny. To mock me in a time of stress is RUDE. If that's how "most of you would respond" I think you should all consider a different mode of communication.

---

### Post by Bachstelze on 2009-09-16
**Everyone** please calm down, thank you.

---

### Post by Bölvaður on 2009-09-16
This is highly strange.
I guess we have covered most of the tricks to get it to work. Perhaps the problem is too simple to even think of.

The docx file that the guy above me posted worked very well on open office 3.0. I just right clicked it, open as... picked open office and wholla.
I would want you to do 3 different versions of that. Two GUI style, and one CLI style (temrinal).


All you need to do to prepare for this is downloading the file to desktop (save link as..)
This is a must, you must have it on your desktop. It is more reliable and also it will make my terminal command work ^.^

1. GUI
Do exactly like I said and right click &#8594; open as... &#8594; open office.

2. GUI
Open open office writer and drag and drop the file into it.
Alternatively use the open option in open office writer to open the file, it should force it to spew out the interior of the file.

3. CLI - terminal
```
soffice ~/Desktop/**test2.docx**
```

note that Im using the test document provided by mike555, you should try this with that document also, as it seems to be working for all of us.

---

### Post by orlandomike on 2009-12-17
I know that open office can Save As as a docx extension file so it should be able to open it even if by importing.

---

### Post by Nightsurfer on 2009-12-17
For what it's worth, I just did a quick test on this Asus eee pc 900 running Karmic, opened ooo writer (3.1), clicked open document, chose a docx file previously created in MS office 2007 on a PC running Vista Home Basic, and everything happened as it should. Looking back through the thread, The error message posted regarding a zip file error suggests to me that the file in question is not in a valid docx format, may well be corrupt, and the original poster might benefit by learning a little about file transfer mechanisms, anger management and "netiquette". YMMD.

---


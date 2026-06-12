---
title: "Can I install windows programs using Ubuntu"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by jelo1105 on 2009-10-05
hey guys i cannot see the threads im looking for so i post this to this thread sorry for being out of topic. i just want to know if Ubuntu are able to install all application that the windows can? im planning to install ubuntu this weekend but im not sure about it beacause of this pls help.......

---

### Post by jlhaslip on 2009-10-05
In order to run Windows software in Ubuntu, you need to have WINE installed. It is a Windows Emulator that allows *some* Windows software to run inside a Ubuntu OS. 
Not all windows software can be run under WINE, and some might need to be tweaked to suit your specific installation.
What programs do you have in mind?

---

### Post by appoloin on 2009-10-05
[http://www.winehq.org/](http://www.winehq.org/)

---

### Post by tom.swartz07 on 2009-10-05
Well, first of all, welcome to the Ubuntu Community! Im honored to welcome you and reply to your very first post!

In regards to your question, the answer is technically, yes. There is a big emphasis on technically, though. MOST Windows programs, .exe files, will run using a program called Wine. You could get that by opening a terminal and entering ```
sudo apt-get install wine
```

You will run into problems with only certain programs. iTunes is a major example. If you need iTunes for iPod syncing, there are many, many programs that you could use to sync instead. Amarok is probably one of the easiest to use. Other programs could be found here: [Ubuntu Documentation]("https://help.ubuntu.com/community/PortableDevices/iPod")

If you had some examples of programs that you hoped to install, we could give you a better, more specific answer as to what works and what programs will not work.

Thanks for your interest in Ubuntu! Hope to see you around soon!

---

### Post by MelDJ on 2009-10-05
> **jelo1105 said:**
> hey guys i cannot see the threads im looking for so i post this to this thread sorry for being out of topic. i just want to know if Ubuntu are able to install all application that the windows can? im planning to install ubuntu this weekend but im not sure about it beacause of this pls help.......

you can make a virtual windows too with virtualbox: [http://www.virtualbox.org/](http://www.virtualbox.org/) and install all the programmes in there

---

### Post by danrb007 on 2009-10-05
I am new to ubuntu.  I am interested in what wine can do.  My specific program is MS publisher 2003. Or is anyone developing a program to open .pub files. I like openoffice and the freedom of linux.  When I open wine and brouse programs it doesn't show any programs in my windows program files directory. Do I have to reinstall any programs that I want wine to run?

---

### Post by Merk42 on 2009-10-05
> **danrb007 said:**
> I am new to ubuntu.  I am interested in what wine can do.  My specific program is MS publisher 2003. Or is anyone developing a program to open .pub files. I like openoffice and the freedom of linux.  When I open wine and brouse programs it doesn't show any programs in my windows program files directory. Do I have to reinstall any programs that I want wine to run?

Yes, you do need to reinstall them via WINE
However, I'm not sure just how well Office 2003, or more specifically, Publisher, will work under WINE.
[The recent tests](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9715) seem to me that it won't run properly enough

Given it is not a 3d application, and you presumably have a copy of Windows, you could try Virtualbox

Depending on your situation you may want to convert the pub to impress.

---

### Post by ad_267 on 2009-10-05
Everyone has mostly answered your question already, but I'd just like to point out that on Linux you can use Scribus instead of Publisher. It won't open Publisher files, but in my opinion it is a much more polished and useful application if that is not an issue.

Edit: Sorry, I thought I was replying to the original poster. I didn't realise the thread had been hijacked.

---

### Post by starcannon on 2009-10-05
I would suggest a dual boot, if ready access to windows programs is a vital priority, then dual boot is the most compatible method. If you only need windows software, and have no windows only hardware to worry about, then it would also be worth considering exclusive boot for Ubuntu, and run Windows in a virtual machine to get access to those softwares. It may be possible to access some windows only hardware from the vm, but it would be something you would want to verify before making a final decision.

Best of Luck

---

### Post by praveesh on 2009-10-05
I would recommend you install the latest develesodnt version of wine 1.0.29 rather than the latest stable version of wine . The latest develesodnt version supports a lot of softwares that the stable one don't . To install latest development version, visit  [www.winehq.org](www.winehq.org)

---

### Post by Tteddo on 2009-10-05
I'd like to chime in here. I found this great program that automates setting up Wine and installing some programs:
[http://www.playonlinux.com/en/]("http://www.playonlinux.com/en/")
I even have Safari, and Internet Explorer 7 running on Hardy (I am a web dev). It uses Bash and Python to automate it.

---


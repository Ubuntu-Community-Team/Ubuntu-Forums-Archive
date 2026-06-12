---
title: "problem with a terminal script"
date: 2011-03-10
forum: New to Ubuntu
---

### Post by s1wood on 2011-03-10
I have installed the Basic Paye Tools for HMRC, Linux version and it comes with these extra instructions. 

>In order to use the Flash interface (recommended) you will also need to install 
Player and instruct it to trust the Flash content. This can be achieved using the 
following four commands in sequence:  
  
sudo apt-get install flashplugin-nonfree  
  
mkdir -p ~/.macromedia/Flash_Player/\#Security/FlashPlayerTrust 
  
cd ~/.macromedia/Flash_Player/\#Security/FlashPlayerTrust  
  
echo "file:////home/$USER/HMRC/payetools" > payetools.cfg  
  
(Where /home/$USER/HMRC/payetools is the path where you have installed  
PAYE Tools). <

No problem with the first line, I already had Flash anyway but I cannot get the rest to work and I want to check I am doing  this correctly. I am typing in the command and then pressing enter at the end of each line - this just seems to get me back to my user name.
Is there something wrong with this script or have I misunderstood something? 
I have installed the BPT program but  have a  problem getting it to function so I need to know if this is causing the problem.

Susan

---

### Post by nothingspecial on 2011-03-10
That's because you've done it right. The terminal will only tell you if you've done it wrong.

Where did you install the program, have you got the path correct in the last line?

---

### Post by s1wood on 2011-03-10
Yes I'm pretty sure the path is OK. 
This may not be the problem, I'm waiting for someone from HMRC helpdesk to get back to me and I want to be able to tell them I have completed the instructions.
 So if that looks OK it probably is.

thanks

Susan

---

### Post by donkyhotay on 2011-03-10
the command
```

mkdir -p ~/.macromedia/Flash_Player/\#Security/FlashPlayerTrust

```
tells the computer to create a directory while the remaining lines tell the computer to go into that directory to do something. The computer is creating the directory without any problems so doesn't bother to notify you about it and is waiting for the next command. Just continue with the following commands and you should be fine, if you do get an error then of course post that here.

---

### Post by s1wood on 2011-03-11
I've reinstalled the program and gone through the script again. This is what I get - is that what I should expect?

susan@Carrera:~$ mkdir -p ~/.macromedia/Flash_Player/\#Security/FlashPlayer Trust
susan@Carrera:~$ cd ~/.macromedia/Flash_Player/\#Security/FlashPlayer Trust
[email]susan@Carrera:~/.macrom[/email]edia/Flash_Player/#Security/FlashPlayer$ 
[email]susan@Carrera:~/.macrom[/email]edia/Flash_Player/#Security/FlashPlayer$ echo "file:////home/$SUSAN/HMRC/payetools" > payetools.cfg
[email]susan@Carrera:~/.macrom[/email]edia/Flash_Player/#Security/FlashPlayer$ 


HMRC helpdesk doesn't! You'd think if they issue a linux version they'd have someone on the staff who knew something about it! 

Susan

---

### Post by Azdour on 2011-03-11
Hi,

I'm only guessing but:

```
echo "file:////home/$SUSAN/HMRC/payetools" > payetools.cfg
```

should probably be:

```
echo "file:////home/susan/HMRC/payetools" > payetools.cfg
```

---

### Post by nothingspecial on 2011-03-11
> **Azdour said:**
> Hi,

I'm only guessing but:

```
echo "file:////home/$SUSAN/HMRC/payetools" > payetools.cfg
```

should probably be:

```
echo "file:////home/susan/HMRC/payetools" > payetools.cfg
```

That's right, either susan or $USER

many generic instructions will use the $USER variable because those instructions will work for anyone using linux (bash).

$USER is the current user - if you see what I mean

---

### Post by s1wood on 2011-03-11
susan@Carrera:~$ mkdir -p ~/.macromedia/Flash_Player/\#Security/FlashPlayerTrust
susan@Carrera:~$ cd ~/.macromedia/Flash_Player/\#Security/FlashPlayerTrust
[email]susan@Carrera:~/.macrom[/email]edia/Flash_Player/#Security/FlashPlayerTrust$ 
[email]susan@Carrera:~/.macrom[/email]edia/Flash_Player/#Security/FlashPlayerTrust$ echo "file:////home/SUSAN/HMRC/payetools" > payetools.cfg
[email]susan@Carrera:~/.macrom[/email]edia/Flash_Player/#Security/FlashPlayerTrust$ 

Does that make sense now? I'm still not clear what is expected to happen. The program still doesn't work but that may not be anything to do with it.

regards,

Susan

---

### Post by Azdour on 2011-03-16
Hi,

Looking at your terminal prompt:

```
susan@Carrera
```

It looks like your username is susan and not SUSAN. Usernames are case sensitive.

Do you still get an issue if you do the following?:

```
echo "file:////home/susan/HMRC/payetools" > payetools.cfg
```

What the command is doing is outputting the text "file:////home/susan/HMRC/payetools" to a file called payetools.cfg.

---

### Post by iMacUser on 2011-03-23
Hi,

I too have this problem, and having followed all the steps mentioned above, I get as far as seeing the Basic PAYE Tools splash screen for about 2 seconds.  Then the outline of the application window appears for a few seconds before dissapearing.  Then nothing happens.

I'm using Kubuntu 10.04 on an Acer Aspire 5741.

I tried running from the konsole and got the following:

bpt.linux: 1: ELF04: not found
bpt.linux: 2: Syntax error: "(" unexpected

HMRC helpdesk have escalated the problem and "will get back to me"

Any thoughts?

---

### Post by grimbold on 2012-04-03
Hi
I too am trying to install PAYE TOOLS for Linux (and get it to work!).
Hmrc helpdesk asked via email for the set of logfiles listed below

 [COLOR=black][FONT=Times New Roman][FONT=Verdana]bpt-xxx.log (where x is a number)[/FONT][/FONT][/COLOR]
 [COLOR=black][FONT=Times New Roman][FONT=Verdana]bpt-xxx.x.log (where x is a number)[/FONT][/FONT][/COLOR]
 [COLOR=black][FONT=Times New Roman][FONT=Verdana]bpt-dtu-xxx.log (where x is a number)[/FONT][/FONT][/COLOR]
 [COLOR=black][FONT=Times New Roman][FONT=Verdana]bpt-dtu-xxx.x.log (where x is a number)[/FONT][/FONT][/COLOR]
 [COLOR=black][FONT=Times New Roman][FONT=Verdana]bitrock_installer_xxxx.log [/FONT][/FONT][/COLOR]
 [COLOR=black][FONT=Times New Roman][FONT=Verdana]bitrock_debug_xxxx.xml[/FONT][/FONT][/COLOR]

which they said would be in /tmp.  They weren't.
Might be worth having a look to see if you have them.

---


---
title: "Python OpenGL Support"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by Dave.E on 2009-08-07
Hi... I tried this in another Forum, but got no response, so trying again here...
--------------------------------------------------------------------------------
Python OpenGL support 
--------------------------------------------------------------------------------
Wanting to try the 3D chess...
Error says
No Python OpenGL support
No Python GTKGLExt support
I have python installed?
What else do I need and How to I install it?
D. 
     
Re: Python OpenGL support 
--------------------------------------------------------------------------------
I tried installing some Python stuff from the Synaptic Package Manager window.
First the error was reduced to :
"No Python OpenGL support"
So I presume GTKGLExt support is now OK
Then I installed more OpenGL (there seems to be no end, not sure how one is supposed to know what is and isn't needed)
Now the Chess program starts and immediately terminates.
HELP!
Re: Python OpenGL support 
--------------------------------------------------------------------------------
Hello?
Can no one help with this problem?

---

### Post by Eisenwinter on 2009-08-07
```
sudo apt-get install pygame
```

Install PyGame.

I'm not a Python coder in general, so I'm not sure whether the OpenGL library will be included under PyGame.

If it's not try:
```
sudo apt-cache search *python*opengl*
```

Report results.

Also, there's no need to complain that no-one has helped you, if it's only been 30 minutes since you posted the help *request*.

---

### Post by Dave.E on 2009-08-08
Hi...
The first command:  
sudo apt-get install pygame

Brought the following result:

[COLOR=Blue]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pygame[/COLOR]

So I tried the second one:
sudo apt-cache search *python*opengl*


Which brought the following result:
[COLOR=Blue]E: Regex compilation error
dave@dave-desktop:~$ [/COLOR]

So, no go as yet...
Any more Ideas???

---

### Post by Dave.E on 2009-08-09
Any more Ideas out there?

---

### Post by unutbu on 2009-08-09
You might be experiencing this bug: [https://bugs.launchpad.net/ubuntu/+source/pyopengl/+bug/351284](https://bugs.launchpad.net/ubuntu/+source/pyopengl/+bug/351284)

If so, the fix is to enable Robert Ancell's PPA repository:

```

gksu gedit /etc/apt/sources.list.d/robert_ancell_ppa.list

```
Add this line:```

deb http://ppa.launchpad.net/robert-ancell/ppa/ubuntu jaunty main
``` (Change jaunty to whatever version of Ubuntu you are using.)
Save and exit the text editor.
Add his gpg key by typing in the terminal:
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 149D38A7   

```
Then reinstall pyopengl:
```

sudo apt-get update
sudo apt-get install python-opengl
```

---

### Post by Dave.E on 2009-08-09
Where does the file edit end UNUTBO?
You say "Add this line:"... 
It's fairly obvious that you mean add it to the blank file 'robert_ancell_ppa.list' I just created.
But then you say "Add his gpg key:"... 
This time you don't say if that is an addition to the file or if it's a 'real time' command as nowhere do you say to close the edit or where to save the file?

The reason I ask, is that I put it in the file, but then when I ran the command [FONT=monospace]

[/FONT]'sudo apt-get update'

I got the following error:

E: Type &#8216;sudo&#8217; is not known on line 2 in source list /etc/apt/sources.list.d/robert_ancell_ppa.list
dave@dave-desktop:~$ 

Sorry, I'm new to Linux so some of the things you don't need to even think about, I'm completely unaware of.

Dave.

---

### Post by unutbu on 2009-08-09
Dave.E, You are absolutely correct that I was unclear and I did not even realize it. Sorry about that. 

Put this single line in /etc/apt/sources.list.d/robert_ancell_ppa.list:
```

deb http://ppa.launchpad.net/robert-ancell/ppa/ubuntu jaunty main

```
Save and exit the text editor.
Then, in the terminal run the commands
```

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 149D38A7
sudo apt-get update
sudo apt-get install python-opengl
```

---

### Post by Dave.E on 2009-08-09
OK Did that...
Here is the output...

dave@dave-desktop:~$ gksu gedit /etc/apt/sources.list.d/robert_ancell_ppa.list
Altered to contain only one line:
deb [http://ppa.launchpad.net/robert-ancell/ppa/ubuntu](http://ppa.launchpad.net/robert-ancell/ppa/ubuntu) jaunty main

dave@dave-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 149D38A7
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 149D38A7
gpg: requesting key 149D38A7 from hkp server keyserver.ubuntu.com
gpg: key 149D38A7: public key "Launchpad PPA for Robert Ancell" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
dave@dave-desktop:~$ sudo apt-get update
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB [52.6kB]     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_GB          
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_GB              
Get: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg [307B]                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_GB                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_GB      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources              
Get: 3 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release [74.7kB]                        
Get: 4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB [4640B]
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB [35.2kB] 
Get: 6 [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages [3204B]                   
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB [47.5kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB         
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB   
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources             
Fetched 218kB in 10s (21.7kB/s)                                                
Reading package lists... Done
dave@dave-desktop:~$ sudo apt-get install pyopengl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**[COLOR=Blue]E: Couldn't find package pyopengl[/COLOR]**
dave@dave-desktop:~$ 

--------------------------
So same problem still exists.???

---

### Post by unutbu on 2009-08-09
Oh dear. My mistake. Try```


sudo apt-get install python-opengl
```

---

### Post by Dave.E on 2009-08-09
Yup, that worked,
Thank you.
And the 3d chess works fine now.
Cheers,
D.

---

### Post by Cobaltx on 2009-10-23
Hello Dave E, I have had exactly the same problem as you have had with the 3D Chess scenario and I have followed your thread to try and fix the problem. I am completely new to Ubuntu / Linux and I'm not sure whether I can write to you or not but anyway.

This is the code I get when I do what you did:
cobalt@cobalt-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 149D38A7
[sudo] password for cobalt: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 149D38A7
gpg: requesting key 149D38A7 from hkp server keyserver.ubuntu.com
gpg: key 149D38A7: "Launchpad PPA for Robert Ancell" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
cobalt@cobalt-desktop:~$ sudo apt-get update
E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)
cobalt@cobalt-desktop:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 149D38A7
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 149D38A7
gpg: requesting key 149D38A7 from hkp server keyserver.ubuntu.com
gpg: key 149D38A7: "Launchpad PPA for Robert Ancell" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
cobalt@cobalt-desktop:~$ sudo apt-get update
E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)
cobalt@cobalt-desktop:~$ sudo apt-get update
E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)
cobalt@cobalt-desktop:~$ sudo apt-get install python-opengl
E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
cobalt@cobalt-desktop:~$ 

What is the Malformed line 54 stuff about? Should I send this to anyone in  particular?

Cobaltx

---


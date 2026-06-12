---
title: "how to install his software"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by indianhits on 2010-01-04
hello i am new to Linux i have been trying to install this software for almost 1 years i searched whole internet but that gave me error.

[http://rapidshare.com/files/330086241/CyberoamLinuxClient.tar.gz.html](http://rapidshare.com/files/330086241/CyberoamLinuxClient.tar.gz.html)

this is an client software which helps me to login to my ISP's server and use my internet.i tried but did not get it work so i am currently using the .EXE in windows to use internet.please help me

thank you.

EDIT: there is also a README file inside the tarball.

---

### Post by kellemes on 2010-01-04
For those willing/able to figure this out..
Two files.. one executable (crclient) and a README..
```
Usage : ./crclient [OPTION]..[-f filepath]


	-h, --help			 displays the help for Client and exit.
	-l, --logout [Username]		 logout from the current session.
					 When Configured for Multiple-Login Username Required.
	-s, --setpreferences		 Set Preferences for the client.
	-u, --user <username>		 get username at the time of login.
	-f, --filepath <filepath>	 set path for Configuration file.
	-d, --logfilepath <filepath>	 set path for log file. Default:'/var/log/crclient.log'.
	-V, --version			 displays the current version.
	-v, --verbose			 Sets debugging Mode .

			 Either -u OR  -l option is must.


```


```
					README
			
			crclient 1.1 for Unix/Linux

Contents
	* Introduction
	* Make 
	* Options
	* Example of Configuration File


Introduction 
	
	Cyberoam Client is a part of the Cyberoam product which is a complete solution to
	Employee Internet Management. This tool provides an interface for the client to 
	communicate with the Cyberoam server. There are various options provided which help the
	client to effectively communicate with the server.

Make
	crclient supports two modes at the time of compilation. 
	1) Single Login
	2) Multiple Login
		In case of single login only one user is allowed to login at a time. For 
	enabling single mode the macro CFLAGS in the Makefile has to be disabled.
		#CFLAGS=-D__MULTILOGIN__

		In case of multiple login option the more then one user can login at a given 
	time. The macro CFLAGS has to be enabled before making the files.
		CFLAGS=-D__MULTILOGIN__

	Other make options include the clean option. Before making the file after the macro is
	enabled/disabled the clean option should be used.
		Ex.
			$make clean.	
	
Options
	
	-u :	The option is responsible for sending a login request to the server. It requires 
		username as a parameter.

	-s :	The option is for setting preferences for the client. Preferences such as AskonExit,
		AutoLogin, ShowNotification and Server Address can be set using this option. The 
		preference values are then reflected in the Configuration file.
	
	-l:	This option is used to send a logout request to the server. In case of Multiple 
		Login mode this option requires argument i.e Username. 

	-h:	 provides help for the client.

	-d:	Specify the location for log file.

	-v:	Sets the verbose mode on. This option is for debugging purpose. 

	-V:	Provides Current Version information.

	-f: 	Specify the location for the configuration file.

Example of Configuration File

	AskonExit       0
	AutoLogin       0
	FirstTime       1
	Password
	Port    6060
	SavePassword    0
	Server  192.9.203.203
	User    ankit
	ShowNotification        1
	LiveRequestTime 180
	AlreadyLoggedIn 0
	VersionId       1
	Version crclient1.1
	
	The configuration file includes the above showm parameters. First Configuration file is searched
	at /etc, if not found  it is searched in the user's home directory. If the configuration file is 
	not found at both the places a file is created in the user's home directory by accepting the 
	essential parameters from the User.
 
NOTE : 

i)	User has to manually disable the SavePassword option in the configuration file by setting the 
	value of SavePassword field to zero , once the option is enabled.

ii)	Also, if the savepassword option is enabled and Password field is found to be null in the
	configuration file the user have to disable the savepassword option i.e by setting the
	SavePassword field to 0, inoder to login.

iii) If -f option is specified the full path along with the filename should be specified.
	 Ex. /home/ankit/CyberClient.conf.

iv) In case of Sun Solaris the multiple process issue is vulnerable.No gaurantee is taken to 
	control multiple client process invocation.

v)  In case of '-d' option if log file cannot be opened at the specified location client exits.
	In absence of '-d' option preference for log location is
	1) '/var/log'
	2) Users home directory
	3) '/tmp'
	If all the three preferences fail logging will be done on standard output.

```

---

### Post by Methuselah on 2010-01-04
First of all be certain that this is the program you need and you trust the source.

What you have to do is run it from a terminal.
After you download it an extract it (right click and choose extract) go into the folder with the extracted files.
Right click on empty space within the folder and choose 'Open Terminal Here'.
Then type 

```

./crclient

```

and hit enter.

My understanding is that it will not find a configuration file and will therefore ask you questions that you'll have to answer such as:
IP address of the server you're connecting to
Your username and your password.

---

### Post by indianhits on 2010-01-04
> **Methuselah said:**
> First of all be certain that this is the program you need and you trust the source.

What you have to do is run it from a terminal.
After you download it an extract it (right click and choose extract) go into the folder with the extracted files.
Right click on empty space within the folder and choose 'Open Terminal Here'.
Then type 

```

./crclient

```and hit enter.

My understanding is that it will not find a configuration file and will therefore ask you questions that you'll have to answer such as:
IP address of the server you're connecting to
Your username and your password.




yes sir i trust the source this software is given by my isp in our clients account
and thanks i will try and reply back the results

once again thanks!!!

---

### Post by indianhits on 2010-01-05
thanks its working but when i log in its that i have logged in but i can't browse internet i guess that's my ISP's problem but still thanks problem solved!!!

still /.crclient what this means.

---

### Post by 3rdalbum on 2010-01-05
> **indianhits said:**
> thanks its working but when i log in its that i have logged in but i can't browse internet i guess that's my ISP's problem but still thanks problem solved!!!

still /.crclient what this means.

crclient is the file name of the program. The ./ says "run this file in the current directory".

---

### Post by indianhits on 2010-01-06
thank you very much!!!

---


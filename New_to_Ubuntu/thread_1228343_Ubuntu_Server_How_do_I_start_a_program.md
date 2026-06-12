---
title: "Ubuntu Server: How do I start a program"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by atomicpurple on 2009-07-31
Yesterday, with the help of youtube, I was able to install ubuntu server, a lamp stack, and joomla.  I ended my day with everything running.  When I quit I was able to key in an ip address that I'd recorded from a windows machine and "work" (although this is all play for me).  

At day's end I logged out and shut down my new ubuntu server.  

Today, I powered the box back up, attempted to logon to the ip address from my windows machine and nothing.  

I logged into my ubuntu server, tried the commands that I gleaned from varying cheat sheets on the internet, but nowhere can I figure out how to start/run the programs (lamp, joomla) that I need.  

Asking this question is embarassing, but I promised I tried, I really did.  Can anyone help this linux server challenged Clevelander?

---

### Post by BDNiner on 2009-07-31
Did you assign a static IP address? Or is it DHCP? Are you having an issues connecting to the server? or can you log into the server but can't run any applications?

---

### Post by atomicpurple on 2009-07-31
> **BDNiner said:**
> Did you assign a static IP address? Or is it DHCP? Are you having an issues connecting to the server? or can you log into the server but can't run any applications?

I'll answer you to the best of my limited ability.

I did not assign an ip address.  I don't know what dhcp is, so I don't think I did it.  The youtube video had me record the results of ifconfig.  Right now ifconfig reports 192.168.0.102, which is what I was trying to hit with my windows browser. 

When I get to that ip address, I see "It Works!".  I just don't know how to get into joomla and/or if the programs required to run it are actually running.  I don't know if the lamp stack and joomla run at power up, but I doubt it.

So I'm trying to figure out how to run a program.  I still remember the dos days, so I don't know if that's a help or hindrance.

I am able to logonto the server with the user name and password I used when I set it up yesterday, but just don't know what to do once I'm in.

Thanks, Bill

---

### Post by aesis05401 on 2009-07-31
The 'ps' command with proper options will show you what is running.  Please see the man page on ps as this will help you in many situations: type 'man ps' at a terminal to view the help file.

If the programs are really not started, then you can type 'man <program-name>' to see all the different ways to invoke the program from command line - usually the name of the program followed by some options.

Does this help?

Edit: In 'man' files the usage summary is usually under the 'SYNOPSIS' section near the top of the file.  Then you read further down to find out the meaning of specific options that you can set when launching the program.  There is usually a 'SEE ALSO' section at the bottom of man files that will show you names of related tools to research if you want more understanding.

---

### Post by wojox on 2009-07-31
Joomla usually creates a directory inside documentroot so try 

[http://192.168.0.102/Joomla](http://192.168.0.102/Joomla)

or

[http://192.168.0.102/joomla](http://192.168.0.102/joomla)

If you get "It Works" then Apache and php are running. You just need to find that Joomla directory.

---

### Post by atomicpurple on 2009-07-31
> **aesis05401 said:**
> The 'ps' command with proper options will show you what is running.  Please see the man page on ps as this will help you in many situations.  One key is that ps defaults to effective user id of person entering the command so you need to be sure you are using sudo if you want to see info on root processes. 

If the programs are really not started, then you can type 'man <program-name>' to see all the different ways to invoke the program from command line - usually the name of the program followed by some options.

Does this help?

Edit: In 'man' files the usage summary is usually under the 'SYNOPSIS' section near the top of the file.  Then you read further down to find out the meaning of specific options that you can set when launching the program.  There is usually a 'SEE ALSO' section at the bottom of man files that will show you names of related tools to research if you want more understanding.

I'm kind of stuck.  I am able to login using the user name and password that I created.  When I attempt to logon as root, using either a CR or a blank, I get login incorrect.  During setup I used only one password consistently throughout as this is a learning experience, not a producttion environment.

I just sudo ps'd and the results were login and ps.  Just a ps returned bash and ps.

When I key sudo man apache OR man apache I get no manual entry for apache.

Thanks, Bill

---

### Post by atomicpurple on 2009-07-31
> **wojox said:**
> Joomla usually creates a directory inside documentroot so try 

[http://192.168.0.102/Joomla](http://192.168.0.102/Joomla)

or

[http://192.168.0.102/joomla](http://192.168.0.102/joomla)

If you get "It Works" then Apache and php are running. You just need to find that Joomla directory.

Dude you're dead on!  That worked.

I obviously have a lot to learn.

Do programs loaded just run without being invoked then?

---

### Post by wojox on 2009-07-31
If you can get access your server through PuTTY or what ever your using type:

```
cd /var/www/
```

Look at where joomla is and remember it's exact name.

---

### Post by wojox on 2009-07-31
Yes they do That's how LAMP is configured on a server.

---

### Post by aesis05401 on 2009-07-31
I should have mentioned that the -e flag would be a good one to start with for ps. 

Glad you got it working.

---

### Post by BDNiner on 2009-07-31
> **atomicpurple said:**
> I'll answer you to the best of my limited ability.

I did not assign an ip address.  I don't know what dhcp is, so I don't think I did it.  The youtube video had me record the results of ifconfig.  Right now ifconfig reports 192.168.0.102, which is what I was trying to hit with my windows browser. 

When I get to that ip address, I see "It Works!".  I just don't know how to get into joomla and/or if the programs required to run it are actually running.  I don't know if the lamp stack and joomla run at power up, but I doubt it.

So I'm trying to figure out how to run a program.  I still remember the dos days, so I don't know if that's a help or hindrance.

I am able to logonto the server with the user name and password I used when I set it up yesterday, but just don't know what to do once I'm in.

Thanks, Bill

Since you get the page "it works" when access the ip in a web browser then you have the LAMP part setup correctly. At least Apache is up and running. My SQL and Python are installed to? How were you connecting when you first installed the software?

---

### Post by atomicpurple on 2009-07-31
> **aesis05401 said:**
> I should have mentioned that the -e flag would be a good one to start with for ps. 

Glad you got it working.


Thanks to all for your help.  You'll be seeing me back here again.  I don't give up easily and this is kinda nerdy, but way fun.  Bill

---


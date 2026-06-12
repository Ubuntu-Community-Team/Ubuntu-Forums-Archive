---
title: "Package Operation failed"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by sealev on 2011-06-10
Hi
I have 11.04 and all installation went perfect.
Now I was trying to get SW updates and I get an Error msg: 
"Package Operation failed
The Installation or removal of a software package failed"
In the details I have to follow:

installArchives() failed:  Extracting templates from packages: 20%% Extracting templates from packages: 41%% Extracting templates from packages: 61%% Extracting templates from packages: 82%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 20%% Extracting templates from packages: 41%% Extracting templates from packages: 61%% Extracting templates from packages: 82%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
 Extracting templates from packages: 20%% Extracting templates from packages: 41%% Extracting templates from packages: 61%% Extracting templates from packages: 82%% Extracting templates from packages: 100%% 
Preconfiguring packages ... 
Setting up tzdata (2011g-0ubuntu0.11.04) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 tzdata 
Setting up tzdata (2011g-0ubuntu0.11.04) ... 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $reply in scalar chomp at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 66. 
Use of uninitialized value $reply in concatenation (.) or string at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 67. 
Use of uninitialized value $reply in split at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 68. 
Use of uninitialized value $ret in string eq at /usr/share/perl5/Debconf/FrontEnd/Passthrough.pm line 109. 
dpkg: error processing tzdata (--configure): 
 subprocess installed post-installation script returned error exit status 128 


I was also trying to download a SW (graphics) and I got the same...

Would appreciate support on that.

---

### Post by Rubi1200 on 2011-06-11
Hi and welcome to the forums :-)

Open a terminal and run the following commands:

```
sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get update
```

If you get errors with any or all of the commands, post the output here as you did before.

Thanks.

---


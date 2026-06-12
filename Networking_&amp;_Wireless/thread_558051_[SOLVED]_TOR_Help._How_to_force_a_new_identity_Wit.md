---
title: "[SOLVED] TOR Help. How to force a new identity? Without Vidalia."
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by Sp|ke on 2007-09-23
Asked elsewhere and searched for ever! So a thread of it's own.....

I'm trying to work out how to force TOR to change it's routing/identity when I want it to (a la vidalia). It's trivial enough to restart it and consequently get a different path using

```

sudo /etc/init.d/tor restart

```

but thats less than ideal. I've gone through the man pages/online help/docs etc etc etc and unless I'm being blind I cant find it for the life of me.

This is specifically for **IRC** use as Dalnet among others K-Line a huge number of the exit nodes thanks to the idiots who abuse it :( So plugins for FF etc aren't really what I need. 

Any help most apreciated cheers!

---

### Post by Sp|ke on 2007-09-23
Ok I'm officially nub of the week I think. (Using it for IRC and I never thought to ask in #tor go figure :/ )

For anyone interested to know you need to telnet into Tor's control port and send "signal newnym" to make Tor switch to clean circuits.

S

---

### Post by v.. on 2007-10-04
thanks for the info with tor and privoxy in the step by step threads.

can you tell me how do i telnet into something? thanks

---

### Post by Sp|ke on 2007-10-06
No problem v..

I'm assuming you want to telnet into Tor 

First you need to make sure that Tors control port is enabled (default as port 9051)
Open a terminal and type

```

sudo vi /etc/tor/torcc

```

Then uncomment the line
```

#ControlPort 9051

```

This enables the control port, allowing you to send commands via telnet like so: (again from the terminal)

```

telnet 127.0.0.1 9051

```

This will give you the prompt
```

Escape character is '^]'.

```

From there you can send any of the commands contained in the control spec
[http://tor.eff.org/svn/trunk/doc/spec/control-spec.txt](http://tor.eff.org/svn/trunk/doc/spec/control-spec.txt)

Lets assume you want (as I did ) to force a clean path, then do the following:

```

telnet 127.0.0.1 9051
Escape character is '^]'. # [console output]
AUTHENTICATE
250 OK                                # [console output]
signal NEWNYM
250 OK                                # [console output]
quit

```

If you want to automate this and you have **expect** installed then a small script for you:

```

#!/usr/bin/expect -f
# telnet into tor and get clean path using expect

spawn telnet 127.0.0.1 9051
expect "Escape character is '^]'."
send "AUTHENTICATE\r"
expect "250 OK"
send "signal NEWNYM\r"
expect "250 OK"
send "quit\r"

# eos

```

Hope that helps, and please excuse the slightly stilted way this is written as I'm a total noob with linux, but I point blank **refuse** to "upgrade" (?????) to Vista bleugh... 

S.

---

### Post by jeffstatin on 2007-10-27
Hi,

There is a major security risk to keeping the control port open without authentication requirements.  There have been tested attacks where an adversary can change your torrc and hup your Tor without your knowledge; very dangerous.  The values HashedControlPassword or CookieAuthentication should be set in the torrc, see [https://www.torproject.org/tor-manual-dev.html.en](https://www.torproject.org/tor-manual-dev.html.en) (same applies for stable Tor versions).

Which brings me to my question about using NEWNYM when CookieAuthentication|1 is set and there already exits a magic cookie ( ~/.tor/control_auth_cookie)...

I am trying (and failing) to write a bash script to automate the process of hexing the magic cookie contents and using it with telnet.  To send a signal to Tor when a magic cookie is present the script needs to hexadecimal encode  the contents of the magic cookie and pass that output to AUTHENTICATE as so:

> 
telnet 127.0.0.1 9051
Escape character is '^]'.
AUTHENTICATE **<Hexed_Cookie_Contents_Here>**
250 OK
signal NEWNYM
250 OK
quit


[i]
Anyone have a solution or suggestions?[/i] 


I want to use the  cookie method because it is more portable, if someone was only going to use the script on their own Tor they could set control port auth by password and  specify that with AUTHENTICATE during telnet.

> **Tor Man**
[https://www.torproject.org/tor-manual-dev.html.en](https://www.torproject.org/tor-manual-dev.html.en)

CookieAuthentication 0|1
If this option is set to 1, don't allow any connections on the control port except when the connecting process knows the contents of a file named "control_auth_cookie", which Tor will create in its data directory.

> **Tor Specs.**  section 5.1
[https://tor-svn.freehaven.net/svn/tor/trunk/doc/spec/control-spec.txt](https://tor-svn.freehaven.net/svn/tor/trunk/doc/spec/control-spec.txt)

5.1. Authentication

By default, the current Tor implementation trusts all local users.

If the 'CookieAuthentication' option is true, Tor writes a "magic cookie" file named "control_auth_cookie" into its data directory.  To authenticate, the controller must send the contents of this file, encoded in hexadecimal.



Thank  you

---

### Post by jeffstatin on 2007-10-28
Hi wje_lf,

Thank you for the link, it confirmed my assumptions.  I wrote a couple of lines to try and automate the process but as I'm fairly new to bash scripting I did not get it right...I'm still trying to figure it out by trail and error.   (I didn't add any  exit codes, etc, yet as I wanted to make it work first.)

Would you mind  looking over these lines?  I'm pretty sure I did not write the variable with CAT correctly, nor the use of the variable with AUTHENTICATE.  

```

cd ~/.tor
# http://www.warpspeed.com.au/Products/OS2/GU/Manual/hexdump.htm
hexdump control_auth_cookie >>hex_cookie_output.txt

# Set variable of magic cookie hex dump using CAT
HEX_COOKIE="cat $hex_cookie_output.txt"

telnet 127.0.0.1 9051	
# Is the following line needed?
Escape character is '^]'.
# Use magic cookie hex dump variable w/authenticate
AUTHENTICATE "HEX_COOKIE"
250 OK
signal NEWNYM
250 OK
quit

```



Another issue is that 'hexdump' has an output like:```

0000000 fce4 cb66 1640 d895 9a5b f12c 3ed6 c075
0000010 d4dc c325 4dc7 b33b b82c 02cd e08b c752
0000020
```
...and Tor expects the following hex format with AUTHENTICATE.  Should I use a different hex dumping tool?  Is there a command or app  to remove white space, etc, from 'hexdump' output? ```
AUTHENTICATE ee10875cb04a837374918510d75ff600f85abc04a33fda23895954dcd69a6a3b
```


Thank you!

---

### Post by Sp|ke on 2007-10-30
Jeff, forgive me if I'm barking up the wrong tree, but I'm worried that my earlieir post was slightly in error in it's context (mainly due to my bad explanation, edited it now to make it a little clearer I hope.)

```

telnet 127.0.0.1 9051	
Escape character is '^]'.  ## This line is the consoles o/p ie NOT a command
AUTHENTICATE
250 OK                                   ## likewise this one
signal NEWNYM
250 OK                                   ## and this one
quit

```

As for the security concern with an open control port it's not something I was aware of, although I should have been, so thanks for that.

Finally I'm not sure that you can do what you want directly in bash, since you need interaction with the scripts o/p (ie the lines I highlighted above) which is why I used **expect** but please dont worry about proving me wrong though :D

```

sudo apt-get install expect

```

**Expect** is very powerful and allows you to automatically interact with console outputs, the MAN pages are a pig but well worth learning. The script in my post above should get you started.

I'll have a look at the cookie authentication and see if I can work out how to do it (but bear with me I'm a complete noob :D )

---

### Post by Sp|ke on 2007-10-30
**Partial** solution using HashedControlPassword rather than MagicCookie.

Edit torcc adding the hashed password (You can compute the hash of a password by running "tor --hash-password password".)

EG:
```

HashedControlPassword 16:5CDA53BCA4E9269660CCEDAC978063056C478E34A9D339D32981051592 

```

Then use the following **expect** script to force a new path.

```

#!/usr/bin/expect -f
# telnet into tor and get clean path using expect

spawn telnet 127.0.0.1 9051
expect "Escape character is '^]'."
send "AUTHENTICATE 16:5CDA53BCA4E9269660CCEDAC978063056C478E34A9D339D32981051592\r" # my hashed passsword
expect "250 OK"
send "signal NEWNYM\r"
expect "250 OK"
send "quit\r"

# eos

```

Hopefully that should work. I'll have a look at doing it with the cookie hash when I get a spare minute.

[edit]
Just re-read your post and realized you want the cookie method for portability, the above should work with the cookie hex **if** someone can work out how to read the cookie data.
[/edit]


S

---

### Post by Sp|ke on 2007-11-02
**_Cookie Authentication Method_**

This needs work. It should work fine but gives 515 AUTHENTICATON erors :confused:
Two script, first bash script calls second expect script.

```

#!/bin/bash
 
# Script will exit after 20 seconds
set timeout 20
# Move into Tor data directory
cd ~/.tor
# Set variables:
#-------------------------------------------------------------------------------------------
# Set hexdecimal dump of "control_auth_cookie" as variable "HEX_COOKIE"
hexCookie=$(echo $(hexdump control_auth_cookie | sed -e 's/^.......//') | sed -e 's/ //g')
# Set variable for the address Tor listlens on
torAddy='localhost'
# Set variable for the port Tor listlens on (Control Port)
torPort='9051'
# Set variable for the signal to be used (default is NEWNYM)
signal='NEWNYM'
#-------------------------------------------------------------------------------------------
# Run expect and use it to run the script "expect-telnet-signal.exp"
expect -f expect-telnet-signal.exp $hexCookie $torAddy $torPort $signal

```

```

#!/usr/bin/expect -f

# set to 1 to force conservative mode 
set force_conservative 1
if {$force_conservative} {
	set send_slow {1 .1}
	proc send {ignore arg} {
		sleep .1
		exp_send -s -- $arg
	}
}

# Script will timeout after 60 seconds
set timeout 20
# First argument is assigned to the variable hexCookie
set hexCookie [lindex $argv 0]
# Second argument is assigned to the variable torAddy
set torAddy [lindex $argv 1]
# Third argument is assigned to the variable torPort
set torPort [lindex $argv 2]
# Fourth argument is assigned to the variable signal
set signal [lindex $argv 3]

# Expect will launch a telnet session to Tor via. Spawn
spawn telnet $torAddy $torPort
match_max 100000
# Response expected by Expect
expect -exact "Trying 127.0.0.1...\r
Connected to localhost.\r
Escape character is '^\]'.\r
"
# Authenticate use of Tor control port by sending contents of Tor "magic cookie" in hexidecimal format to Tor
send -- "AUTHENTICATE $hexCookie\r"
expect -exact "AUTHENTICATE $hexCookie\r
250 OK\r
"
send -- "d"
expect -exact " "
# Send a signal to Tor
send -- "signal $signal\r"
expect -exact "signal $signal\r
250 OK\r
"
# Close telnet and expect session
send -- "quit\r"
expect eof

```

Unfortunately this gives the following error as mentioned before, but I can't see why..

```

spawn telnet localhost 9051
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
AUTHENTICATE fe7c8343dccb3211c513a685f0b7bc9a4f15c8254b61ccd6011e73bf7069a609
515 Authentication failed: Authentication cookie did not match expected value.
Connection closed by foreign host.

```

S

---

### Post by Sp|ke on 2007-11-03
[SIZE="5"]**_[COLOR="Blue"]Cookie Authentication SOLVED[/COLOR]_**[/SIZE]

The latest Tor alpha comes with a control script written by Stefan Behte which implements secure access to the control port via either cookie or hashed password.

[http://ge.mine.nu/tor-ctrl.html](http://ge.mine.nu/tor-ctrl.html)

Force a new path using
```

/path/to/tor-ctrl -v -c "signal NEWNYM"

```

I would still like to get the previous code example to work, if anyone has got any ideas where it's going wrong I would be very gratefull.

S

---

### Post by jeffstatin on 2007-11-03
Hi,

thanks for the link I'll look into it...but...

> I would still like to get the previous code example to work, if anyone has got any ideas where it's going wrong I would be very gratefull.

I found the problem with my script, I was calling hexdump incorrectly, now fixed.  These scripts work with stable and alpha Tor.  I'm going to re-write the following scripts so the bash part uses Kdialog.  I'm going to call it "expertTorKontrol" (for KDE) and it will allow the use of any signals via. drop down menu and other advanced options not offered by vidalia.  Maybe you could use zanity to do the same for ubuntu with my scirpts?

The first script "bash_signal.sh" runs hexdump to get hexdecimal output of "control_auth_cookie" which it sets to a variable along with variables for the Tor ControlPort, ControlListlenAdress (IP only) and the signal  to  send (e.g. NEWNYM).

The second script "expect_signal.exp" is the script to make expect telnet into Tor, authenticate w/magic cookie contents, send signal and quit.


1. _Packages you may need to 'apt-get install':_
"expect"  -application used to automate telnet sessions into Tor
"expectk"  -containes application called 'spawn', used by expect to launch an app
"hexdump" -application  used to dump hexdecimal contents of Tor magic cookie
"libicu36-dev"  -used by unconv by way of hexdump for dumping hexdecimal value of Tor magic cookie 


2. _Scripts:_
(put both scripts into same dir and edit the location of your magic cookie if requried.  Run bash_signal.sh which calls expect_signal.sh.)

**"bash_signal.sh"**
```

#!/bin/bash

# -UNFINISHED BUT WORKING-
# Script written by Jeffery Statin 10-30-07

# Script will exit after 20 seconds
set timeout 20

# Set chmod permissions for Tor datadir and magic cookie
#----------------------------------------------------------
# Set permissions of Tor's datadir ~/.tor
sudo chmod 744 ~/.tor
# Set permissions of Tor's magic cookie 
sudo chmod 644 ~/.tor/control_auth_cookie
#----------------------------------------------------------

# Set variables:
#----------------------------------------------------------
# Set hexdecimal dump of "control_auth_cookie" as variable "hexCookie"
hexCookie=$(echo $(hexdump -e '/1 "%02x"' ~/.tor/control_auth_cookie))
# Set variable for the IP address Tor listlens on (ControlListenAddress)
torAddy='localhost'
# Set variable for the port Tor listlens on (ControlPort)
torPort='9051'
# Set variable for the signal to be used (default is NEWNYM)
signal='NEWNYM'
#----------------------------------------------------------

# Call expect to run the script "expect_signal.exp" with variables 
expect -f expect_signal.exp $hexCookie $torAddy $torPort $signal

exit 1
```


**"expect_signal.exp"**:
```

#!/usr/bin/expect -f

# Force conservative mode.
set force_conservative 1
if {$force_conservative} {
	set send_slow {1 .1}
	proc send {ignore arg} {
		sleep .1
		exp_send -s -- $arg
	}
}

# Script will timeout after 60 seconds
set timeout 60

# Set variables for expect:
#-------------------------------------------
# First argument is assigned to the variable hexCookie
set hexCookie [lindex $argv 0]
# Second argument is assigned to the variable torAddy
set torAddy [lindex $argv 1]
# Third argument is assigned to the variable torPort
set torPort [lindex $argv 2]
# Fourth argument is assigned to the variable signal
set signal [lindex $argv 3]

# Expect will launch a telnet session into Tor via. Spawn
#-------------------------------------------
spawn telnet $torAddy $torPort
match_max 100000
# Response expected by Expect
expect -exact "Trying 127.0.0.1...\r
Connected to localhost.\r
Escape character is '^\]'.\r
"
# Authenticate contorl of Tor control port w/hexdecimal contents of magic cookie
send -- "AUTHENTICATE $hexCookie\r"
expect -exact "AUTHENTICATE $hexCookie\r
250 OK\r
"
send -- "d"
expect -exact " "
# Send a signal to Tor
send -- "signal $signal\r"
expect -exact "signal $signal\r
250 OK\r
"
# Close telnet and expect session
send -- "quit\r"
expect eof
```

Let me know how it works for you ;) (script copy/paste should  work fine)

---

### Post by jeffstatin on 2007-11-03
Hey,

I just re-read the thread and noticed your posts, sorry I didn't respond sooner, I didn't think anyone was interested. I read your use of password, that's ok if you know the password but not too portable.

Also, it looks like my [**post #9**]("http://ubuntuforums.org/showpost.php?p=3693443&postcount=9") is listed as being posted by you?  do you see that also? wierd

thanks

---

### Post by Sp|ke on 2007-11-04
> **jeffstatin said:**
> Hey,

I just re-read the thread and noticed your posts, sorry I didn't respond sooner, I didn't think anyone was interested. I read your use of password, that's ok if you know the password but not too portable.

Also, it looks like my [**post #9**]("http://ubuntuforums.org/showpost.php?p=3693443&postcount=9") is listed as being posted by you?  do you see that also? wierd

thanks

Nah it was posted by me, yours is [post #11]("http://ubuntuforums.org/showpost.php?p=3698672&postcount=11"), I think we both found the code examples and modified them in slightly different ways (the expect script works fine but the bash script that calls it needed work which you did. Mine was unsuccesful as I didn't filter the hexdump cookie output correctly)

Haven't had time to try your script yet as I'm *supposed* to be working today :p

Re: your PM I would be interested in seeing the menu driven script if you do develop it. As much as I like vidalia it is difficult to get working on Ubuntu and it would be nice to easily show the TOR route, list of available nodes etc etc from a script.

Cheers.

---

### Post by jeffstatin on 2007-11-04
Hey,

> Nah it was posted by me, yours is post #11, I think we both found the code examples and modified them in slightly different ways (the expect script works fine but the bash script that calls it needed work which you did. Mine was unsuccesful as I didn't filter the hexdump cookie output correctly)

Funny...where did you find those two scripts in post #9?  I only as because I wrote both of them.  That's why I thought the post was mine...I recognized my scripts.  The bash I wrote from scratch and the expect script I created using 'autoexpect' (I lightly modified the output script with comments, etc).  The only place I remember posting them was in #tor on IRC, just curious if they've turned up elsewhere?

The controller I'm going to make may not do any node/circuit interaction, I use Vidalia for that.  My controller is going to provide useful functions Vidalia currently does not such as  torrc options, signals and maybe a few other things.   The main reason I made those scripts was to include them in a firefox extension I'm making.  The extension will clear HTTP/S session data from Firefox and clear the cache of Polipo, it will then send a NENYM signal. (If NEWNYM signal is used then the Polipo cache and HTTP/S data in web browser should be cleared to prevent association of pseudonym identities).

What issues are you having with Vidalia?  I run kubuntu and my vidalia runs great.  I compile my own vidalia but I've tested the one in the repo and it works fine too.

p.s. enjoy your day off!

---

### Post by Sp|ke on 2007-11-04
They appear at pastebin [**_755349_**]("http://pastebin.ca/755349") and [**_755350_**]("http://pastebin.ca/755350") respectively. I guess someone cut and pasted them there from #tor.

With regard to vidalia problems, the main issue I **had**, although solved eventually, was that tor was set up to autostart and vidalia starts it up anyways with its own configuration file so I needed to disable tor autostarting, As well as a few other tweaks and fiddles to get it working properly since tor is owned by root. Since I only really used vidalia to rehash a new route (ID) I dumped it in favour of the first quick and dirty expect script I wrote at  [**_post 4_**]("http://ubuntuforums.org/showpost.php?p=3484732&postcount=4").

But now you started me tinkering with [zenity]("http://freshmeat.net/projects/zenity") :D trying to create a nice simple GUI for it. (I needed to learn a little more scripting anyway so thanks!)


> The controller I'm going to make may not do any node/circuit interaction, I use Vidalia for that. My controller is going to provide useful functions Vidalia currently does not such as torrc options, signals and maybe a few other things. The main reason I made those scripts was to include them in a firefox extension I'm making. The extension will clear HTTP/S session data from Firefox and clear the cache of Polipo, it will then send a NENYM signal. (If NEWNYM signal is used then the Polipo cache and HTTP/S data in web browser should be cleared to prevent association of pseudonym identities).

Sounds very interesting, I look forward to seeing it ;) I'm going down a slightly different route since I'm only experimenting for use with IRC so at the moment I am only interested in new ID's and maybe the routing path/exit node.

P.S I ended up doing some real work eventually, but thanks anyway :D

Spike.

---

### Post by achims311 on 2008-02-12
> **Sp|ke said:**
> 

This needs work. 
....
Unfortunately this gives the following error as mentioned before, but I can't see why..

```

AUTHENTICATE fe7c8343dccb3211c513a685f0b7bc9a4f15c8254b61ccd6011e73bf7069a609

```

S

The reason is hexdump uses 2 byte, but you need one byte alignment.
Means you have
fe7c8343...
but need would be
7cfe4383...

Solution is:
```

...
hexCookie=$(hexdump -e '32/1 "%02x""\n"' control_auth_cookie)
...

```

---

### Post by marshal on 2008-03-17
hi, i realy like the scripts to pick a new identity.

i am trying to ad an extra option, were it checks the exitnode.

is there a signal i can use, wich tells me the nick of the current exitnode?

i tried some php code 

<?php echo ($_SERVER["REMOTE_ADDR"]); ?>
and
<?php echo ($_SERVER["REMOTE_HOST"]); ?>

but as you know, you cant get the nick from these infos.


the goal of this would be:
get a new identity with your scripts, check the speed with my script and if the speed is ok, keep the identity (getting the exitnode's nick would make it possible to create a list of good exitnodes and excludenodes).

---


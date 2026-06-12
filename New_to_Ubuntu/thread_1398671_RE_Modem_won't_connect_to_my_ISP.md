---
title: "RE: Modem won't connect to my ISP"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by Dan Flanagan on 2010-02-04
This is what I see when I try to connect...


dflanagan@ubuntu:~$ wvdial
--> WvDial: Internet dialer version 1.60
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT4432444055
--> Waiting for carrier.
ATDT4432444055
CONNECT 38666
--> Carrier detected. Waiting for prompt.
--> Connected, but carrier signal lost! Retrying...
--> Sending: ATDT4432444055
--> Waiting for carrier.
User Access Verification
Username: 
Username: [EMAIL="danflan@isp.com"][COLOR=#444444]danflan@isp.com[/COLOR][/EMAIL]
% Username: timeout expired!
NO CARRIER
--> No Carrier! Trying again.
--> Sending: ATDT4432444055
--> Waiting for carrier.
ATDT4432444055
NO DIALTONE
--> No dial tone.
--> Disconnecting at Thu Feb 4 19:41:03 2010
dflanagan@ubuntu:~$ [EMAIL="danflan@isp.com"][COLOR=#444444]danflan@isp.com[/COLOR][/EMAIL]
[EMAIL="danflan@isp.com"][COLOR=#444444]danflan@isp.com[/COLOR][/EMAIL]: command not found
dflanagan@ubuntu:~$
[IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG] [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8775869")   [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8775869") [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8775869") [[IMG]http://ubuntuforums.org/images/buttons/multiquote_off.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8775869") 
Dan Flanagan[[COLOR=#000000]View Public Profile[/COLOR]]("http://ubuntuforums.org/member.php?u=1007363")[[COLOR=#000000]Send a private message to Dan Flanagan[/COLOR]]("http://ubuntuforums.org/private.php?do=newpm&u=1007363")[[COLOR=#000000]Send email to Dan Flanagan[/COLOR]]("http://ubuntuforums.org/sendmessage.php?do=mailmember&u=1007363")[[COLOR=#000000]Find More Posts by Dan Flanagan[/COLOR]]("http://ubuntuforums.org/search.php?do=finduser&u=1007363")[[COLOR=#000000]Add Dan Flanagan to Your Contacts[/COLOR]]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=1007363")
**[B]******[/B]**[B]******[/B]
[CENTER][LEFT][LEFT] 
Bookmarks
[LIST]
[*][[IMG]http://ubuntuforums.org/images/misc/bookmarksite_digg.gif[/IMG]]("http://digg.com/submit?phrase=2&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1398386&title=Modem+won%27t+connect+to+my+ISP") [[COLOR=#000000]Digg[/COLOR]]("http://digg.com/submit?phrase=2&url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1398386&title=Modem+won%27t+connect+to+my+ISP")
[*][[IMG]http://ubuntuforums.org/images/misc/bookmarksite_delicious.gif[/IMG]]("http://del.icio.us/post?url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1398386&title=Modem+won%27t+connect+to+my+ISP") [[COLOR=#000000]del.icio.us[/COLOR]]("http://del.icio.us/post?url=http%3A%2F%2Fubuntuforums.org%2Fshowthread.php%3Ft%3D1398386&title=Modem+won%27t+connect+to+my+ISP")
[/LIST][/LEFT]
[/LEFT]
[/CENTER]

---

### Post by nhasian on 2010-02-04
hmm you could try lowering the speed of the connection to see if you can stay connected.  instead of 38666 try 28.8k or 33.6k

---

### Post by lkraemer on 2010-02-04
Will you post the listing for your file: /etc/wvdial.conf
```

sudo wvdialconf /etc/wvdial.conf

```
will allow you to edit it.  Just cut and paste it in a posting.
If you have more than one wvdial.conf file, delete the extras, or specify
the file with:
```

wvdial /etc/wvdial.conf

```
 
You may need to set up the pap-secrets and/or chap-secrets file by running the following in a Terminal Window:
```

sudo pppconfig

```
You will need your userlogin, password, ISP provider information, and
pap or chap information for the connection. (You can set up pap and
then chap, if pap doesn't work.) Basically you just answer the questions
that are presented. You can delete a configurations and start over if
you need to from the menu selections.

For more information try this in a terminal window:
```

man pppd
man pppconfig

```

You should have a wvdial configuration file like this at
/etc/wvdial.conf (you may need to add a few things...)

wvdial.conf contains:
```

[Dialer Defaults]
Auto DNS = yes
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
Baud = 48800
New PPPD = yes
Stupid mode = yes
;carrier check = no
Modem = /dev/ttyACM0
ISDN = 0
Phone = 4460568
Password = yourpassword
Username = yourusername@yourisp.net

```

Since you are dialing out, getting the carrier and then the connection is
dropped, most likely your ppp configuration is incorrect.

You can also try pon and poff to make a connection.
```

man pon
man poff

```
for more information

lk

---


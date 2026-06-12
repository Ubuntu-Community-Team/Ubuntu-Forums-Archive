---
title: "Doing #Ubuntu channel with IRC and IRSSI?"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by honeybear on 2011-08-17
Hi, 

So how to configure IRSSI onto irc.freenode.net to get it working from settings for each instance of IRSSI? 

 

```
$ irssi

# then type: 

/SET nick <username> 
/SET alternate_nick <username> 
/SET user_name <username> 
/SET real_name <username> 

/SERVER ADD -ssl -auto irc.freenode.net -p 6697 
/NETWORK ADD -autosendcmd "/^msg nickserv identity <username> <password>;wait 2000" 
/channel add -auto #ubuntu

/save 
```

and then it works forever at each time you type into konsole : irssi !! 
Is it right? If you have any help, please be clear or please give the commands to type directly.. (newbies - oriented)

---

### Post by andrew.46 on 2011-08-19
I wrote quite a comprehensive guide for this a while back, perhaps it will be useful to you:

[Howto] Setup irssi and join #ubuntu on Freenode
[http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

---

### Post by honeybear on 2011-08-21
> **andrew.46 said:**
> I wrote quite a comprehensive guide for this a while back, perhaps it will be useful to you:

[Howto] Setup irssi and join #ubuntu on Freenode
[http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

thank you

Your post is out-dated.

1) this code is not required anymore.
```
mkdir -pv $HOME/.irssi/scripts/autorun && cd $HOME/.irssi/scripts && \
wget http://freenode.net/sasl/cap_sasl.pl && \
cd autorun && ln -sv[COLOR="Red"] ../cap_sasl.pl[/COLOR]
```

Only -ssl and the right port is necessary.

2) the user automatically identified with login and password is not present ... 

There is only the server (out-dated way)... :
```
/network add Freenode
/server add -auto -ssl -ssl_verify -ssl_[COLOR="Red"]capath /etc/ssl/certs [/COLOR]-network Freenode irc.freenode.net 7000
/channel add -auto #ubuntu Freenode
/save
/exit
```

:( :(

---

### Post by honeybear on 2011-08-27
... visibly not much users are using IRSSI and IRC, with freenode.

Anyone? Could you post please the command lines to type to add the IRC IRSSI into the iRSSI configuration please? 

Thank you

---

### Post by andrew.46 on 2011-08-30
> **honeybear said:**
> Your post is out-dated.

Hmmm..... I ran the commands from this guide only recently on a fresh installation of Natty and it certainly logged on securely to #ubuntu with irssi. It did not work for you?

---

### Post by honeybear on 2011-08-31
> **andrew.46 said:**
> Hmmm..... I ran the commands from this guide only recently on a fresh installation of Natty and it certainly logged on securely to #ubuntu with irssi. It did not work for you?

hi,

wow. someone that knows.

Ok, we try from beginning... 


```

cd 
rm -rf .irssi/
## after what you type in konsole or irssi? 
## could you please complete the operations to proceed

```

I am looking forward to hearing you, and thank you in advance

---

### Post by andrew.46 on 2011-09-01
Perhaps simply start at the beginning of the guide and work through it. I tried to write the guide so it had a logical flow and for the most part it is simple copy and paste commands.

---

### Post by honeybear on 2011-09-02
> **andrew.46 said:**
> Perhaps simply start at the beginning of the guide and work through it. I tried to write the guide so it had a logical flow and for the most part it is simple copy and paste commands.

```
cd
rm -rf .irssi
irssi 

```
then 
how to add
"connect -ssl irc.freenode.net"
with automotic login ?

---

### Post by andrew.46 on 2011-09-02
Have you first downloaded the required extras:

```

sudo apt-get -y install irssi irssi-scripts ca-certificates \
libcrypt-blowfish-perl libcrypt-dh-perl libcrypt-openssl-bignum-perl \
libmath-bigint-gmp-perl

```

Some of these of course you will already have...

---

### Post by honeybear on 2011-09-03
> **andrew.46 said:**
> Have you first downloaded the required extras:

```

sudo apt-get -y install irssi irssi-scripts ca-certificates \
libcrypt-blowfish-perl libcrypt-dh-perl libcrypt-openssl-bignum-perl \
libmath-bigint-gmp-perl

```

Some of these of course you will already have...

Thank you it added few packages.

irssi started... so now what should I type to make ssl irc.freenode.net and my username logged automatically both permanents?

---

### Post by andrew.46 on 2011-09-03
The next step should be to not only create an unique username but also to register this username correctly with Freenode. This is all one from within irssi, so first create a username and real name and then connect to Freenode:

```

/set nick <nick> 
/set real_name <Real Name>
/connect irc.freenode.net 8001

```

Obviously you will be putting your own details where I have used brackets, and don't include the brackets themselves. Then register your username with Freenode and make sure the email address is hidden, again these commands are from within irssi:

```

/msg nickserv REGISTER <password> <email>
/msg NickServ SET HIDEMAIL ON

```

Again put your own details in place where I have used brackets and don't include the brackets themselves. Check the final results with the following command from within irssi:

```

/msg nickserv info

```

My own results are as follows:

```

22:08 -!- Starting query in Freenode with nickserv
22:08 <andrew_46> info
22:08 >>> NickServ!NickServ@services.: Information on andrew_46 (account andrew_46):
22:08 >>> NickServ!NickServ@services.: Registered : Mar 18 02:51:30 2008 (3 years, 24 weeks, 
          1 day, 09:13:57 ago)
22:08 >>> NickServ!NickServ@services.: Last addr  : ~andrew@ubuntu/member/andrew-46
22:08 >>> NickServ!NickServ@services.: vHost      : ubuntu/member/andrew-46
22:08 >>> NickServ!NickServ@services.: Last seen  : now
22:08 >>> NickServ!NickServ@services.: Logins from: andrew_46
22:08 >>> NickServ!NickServ@services.: Nicks      : andrew_46 andrew_47
22:08 >>> NickServ!NickServ@services.: Email      : andrew@xxxxxxxxx.org (hidden)
22:08 >>> NickServ!NickServ@services.: Flags      : HideMail, EMailMemos
22:08 >>> NickServ!NickServ@services.: Language   : default
22:08 >>> NickServ!NickServ@services.: *** End of Info ***

```

(I have obscured my email address here.) Note I have registered and alternate username here as well, not required but something to look at later perhaps. If this all goes well the final step will be to setup the SSL/SASL details.

---

### Post by honeybear on 2011-09-03
> **andrew.46 said:**
> The next step should be to not only create an unique username but also to register this username correctly with Freenode. This is all one from within irssi, so first create a username and real name and then connect to Freenode:

```

/set nick <nick> 
/set real_name <Real Name>
/connect irc.freenode.net 8001

```

Obviously you will be putting your own details where I have used brackets, and don't include the brackets themselves. Then register your username with Freenode and make sure the email address is hidden, again these commands are from within irssi:

```

/msg nickserv REGISTER <password> <email>
/msg NickServ SET HIDEMAIL ON

```

Again put your own details in place where I have used brackets and don't include the brackets themselves. Check the final results with the following command from within irssi:

```

/msg nickserv info

```

My own results are as follows:

```

22:08 -!- Starting query in Freenode with nickserv
22:08 <andrew_46> info
22:08 >>> NickServ!NickServ@services.: Information on andrew_46 (account andrew_46):
22:08 >>> NickServ!NickServ@services.: Registered : Mar 18 02:51:30 2008 (3 years, 24 weeks, 
          1 day, 09:13:57 ago)
22:08 >>> NickServ!NickServ@services.: Last addr  : ~andrew@ubuntu/member/andrew-46
22:08 >>> NickServ!NickServ@services.: vHost      : ubuntu/member/andrew-46
22:08 >>> NickServ!NickServ@services.: Last seen  : now
22:08 >>> NickServ!NickServ@services.: Logins from: andrew_46
22:08 >>> NickServ!NickServ@services.: Nicks      : andrew_46 andrew_47
22:08 >>> NickServ!NickServ@services.: Email      : andrew@xxxxxxxxx.org (hidden)
22:08 >>> NickServ!NickServ@services.: Flags      : HideMail, EMailMemos
22:08 >>> NickServ!NickServ@services.: Language   : default
22:08 >>> NickServ!NickServ@services.: *** End of Info ***

```

(I have obscured my email address here.) Note I have registered and alternate username here as well, not required but something to look at later perhaps. If this all goes well the final step will be to setup the SSL/SASL details.

Thank you
Done. Then I found after google that it is the best way to start it.

To start up irssi, at the command line type:

```
irssi -c irc.ircserver.net -n nickname
```


Then how to save it into irssi to allow to startup automatically some given #channels?

---

### Post by andrew.46 on 2011-09-03
Before starting irssi again, and certainly the commandline method you have suggested should work for the moment, you would be best to set the perl script that allows sasl auhentication. Run the following single command from a terminal prompt:

```

mkdir -pv $HOME/.irssi/scripts/autorun && cd $HOME/.irssi/scripts && \
wget http://freenode.net/sasl/cap_sasl.pl && \
cd autorun && ln -sv ../cap_sasl.pl

```

Now start irssi in the manner you have suggested and setup the perl script:

```

/script load cap_sasl.pl
/sasl set Freenode <primary-nick> <password> DH-BLOWFISH
/sasl save
/save

```

(Although when you start irssi the script should autoload anyway.) Then run the following commands from irssi to set up the Freenode connection with ssl and auto-connect to #ubuntu:

```

/network add Freenode
/server add -auto -ssl -ssl_verify -ssl_capath /etc/ssl/certs -network Freenode irc.freenode.net 7000
/channel add -auto #ubuntu Freenode
/save
/exit

```

Now simply start with the command:

```
irssi
```

and if all is well you will make an ssl connection to Freenode and automagically join #ubuntu...

---


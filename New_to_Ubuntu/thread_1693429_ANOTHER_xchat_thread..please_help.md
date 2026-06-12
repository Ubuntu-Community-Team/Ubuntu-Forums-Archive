---
title: "ANOTHER xchat thread..please help"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by SE7EN-LOCSTA on 2011-02-22
I know that there are several of these threads floating around, and I have looked thru several of them.. but I cannot for the life of me get into #ubuntu irc chat. I have been using Ubuntu 10.10 for several weeks now, and have not become real familiar with the command line. 

i have been working at this for several days now, and am not going to be able to rework every step i have attempted, but here is what happens based on my latest attempts. <snip>  is where most of my tries have came from. 

1. sudo apt-get install irssi openssl libcrypt-openssl-bignum-perl libcrypt-dh-perl libcrypt-blowfish-perl 
already isntalled. chekk

2. 

cd ~/.irssi/scripts   here is my first issue. i type this into terminal, and no directory exists. i then make .irssi folder in my home folder, same answer arrives. i then ASSUME that this is going to be for irrsi, so i make xchat 
folder, and then type cd ~/xchat/scripts   this seems to work.
edit: i have showed hidden files, and located the .xchat2 folder, and worked from there also

3. 
sudo mkdir autorun   ;  sudo wget [http://www.freenode.net/sasl/cap_sasl.pl](http://www.freenode.net/sasl/cap_sasl.pl)    ;    cd autorun     ;       
sudo ln -s ../cap_sasl.pl cap_sasl.pl
all seems to be okay


4. load up xchat     
/server add -auto -ssl -network freenode irc.freenode.net 7000     tells me server saved.
/server add -auto -ssl -ssl_cacert /etc/ssl/certs/GandiStandardSSLCA.pem -network freenode irc.freenode.net 7000     * Looking up add
* Unknown host. Maybe you misspelled it?              skip this step

5.                                                         
/sasl set freenode your_nick your_password DH-BLOWFISH  (changing my name and password)  returns error: Unknown Command. Try /help

6. try connect anyways.... 
* Looking up irc.freenode.net
* Connecting to chat.freenode.net (82.96.64.4) port 8001...
* Connected. Now logging in...
* *** Looking up your hostname...
* *** Checking Ident
* *** Couldn't look up your hostname
* *** No Ident response
* *** Notice -- You need to identify via SASL to use this server
* Closing Link: 66.87.2.227 (SASL access only)
* Disconnected (Remote host closed socket).  

try different numbers....
* Looking up irc.freenode.net
* Connecting to chat.freenode.net (213.92.8.4) port 6667...
* Connection failed. Error: (336130315) error:1408F10B:SSL routines:SSL3_GET_RECORD:wrong version number
 Are you sure this is a SSL capable server and port?

i have tried this with enable ssl on/off, and invalid ssl on and off, it still does not work.
 i then tried to manually load the script/plugin of the sasl.pl file from earlier, and i return error   
 Error loading '/home/se7en/.xchat2/cap_sasl.pl':
 Can't locate auto/Irssi/signal_add_.al in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /home/se7en/.xchat2/cap_sasl.pl line 211

i dont know what else to do. ive followed directions to a t, then tried variations on them that i could conjure up, nothing is seeming to work for me. /sasl always gets me an error of unknown command..

if anyone is able to help, i would appreciate it

---

### Post by Nytram on 2011-02-22
Are you just wanting to irc chat in #ubuntu on the freenode network? Because that's easy to do, you just need Xchat, I can give you the steps if you want them. 

Or do you need a secure connection with SSL and SASL, I've personally no idea how that works, maybe someone else can help with that.

---

### Post by SE7EN-LOCSTA on 2011-02-22
yes, that is all i am trying to do :) perhaps i have over complicated things?

---

### Post by Nytram on 2011-02-22
Yeh just a bit ;)

To install xchat you can either use a GUI package manager or in a terminal:

> sudo apt-get install xchat

A menu item will appear for it under Applications/Internet/

When you run xchat youll get a form to fill in the nickname you want to use on irc, here you can also choose Freenode in the networks box.

Then click the connect button to get onto freenode, once youre on type this into the window: **/join #ubuntu** and a new tab will open for that chat room.

You might find this link useful, but if you get stuck post back here.

[https://help.ubuntu.com/community/XChatHowto]("https://help.ubuntu.com/community/XChatHowto")

---

### Post by SE7EN-LOCSTA on 2011-02-23
well. i have clicked on the freenode button.. adn it keeps giving me the same sasl / ssl errors. i have looked at the xchat help pages, to no avail. ive now trid to use pidgin and irssi and am still getting pretty much the same results

---

### Post by andrew.46 on 2011-02-25
If you are still interested in irssi perhaps lok at a guide I wrote a while back:

[Howto] Setup irssi and join #ubuntu on Freenode
[http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

---

### Post by SE7EN-LOCSTA on 2011-02-25
going to end thread. found out from a different place that it was my wireless company blocking the necessary ports. thank you guys for all your time and help, perhaps someone else searching can use this information too :)

---


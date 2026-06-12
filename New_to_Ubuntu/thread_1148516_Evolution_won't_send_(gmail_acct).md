---
title: "Evolution won't send (gmail acct)"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by kmcavoy on 2009-05-04
I just completed a fresh install of Ubuntu 9.04 after one of my kids downloaded something wrong and corrupted the files.  I am trying to re-install the programs I was previously using.  I like Evolution for email and have a pop3 gmail acct that forwards to the Evolution.  Evolution receives gmail great, but it won't send. I get the following message:"Error while saving message to folder."  This happens when I try to save the message as "draft" too.  I pinged gmail to check the connection and all packages were received--no dropped packages.  I have checked by settings for smtp several times to make sure they are correct.  They are:

Server type: SMTP
Server: smtp.gmail.com
checked for server requires authentication
use Secure connection: SSL certification
Type: Plain
Username: <myusername [email]without@gmail.com[/email]>
checked remember password

Any suggestions?  Thanks!

---

### Post by blueridgedog on 2009-05-04
Based on the help here:

[http://mail.google.com/support/bin/answer.py?hl=en&answer=13287](http://mail.google.com/support/bin/answer.py?hl=en&answer=13287)

You have to specify the port of the outbound connection.

---

### Post by kmcavoy on 2009-05-04
Thanks for the link, but I am not for sure how to specify a port.

Thanks,

Kerry

---

### Post by blueridgedog on 2009-05-04
Take a look here:

[http://ubuntuforums.org/showpost.php?p=219269&postcount=2](http://ubuntuforums.org/showpost.php?p=219269&postcount=2)

---

### Post by kmcavoy on 2009-05-04
I have checked around and the various website on how to configure evolution for email from gmail. The articles suggest that I have done it correctly (see: [http://sanaulla.wordpress.com/2008/05/15/configuring-evolution-for-gmail/](http://sanaulla.wordpress.com/2008/05/15/configuring-evolution-for-gmail/)
[http://www.brighthub.com/computing/linux/articles/25196.aspx](http://www.brighthub.com/computing/linux/articles/25196.aspx), [http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/](http://tuxicity.wordpress.com/2007/03/08/howto-set-up-gmail-in-evolution-gnomes-mail-client-and-organizer/)).  There are varying opinions on the type of security encryption (ssl or tsl), but neither works for me.  I really think it isn't my connection between gmail and evolution, but a problem with evolution.  I had evolution set up before without any problems.

Any other thoughts or suggestions?

---

### Post by kmcavoy on 2009-05-04
I just followed the directions from this link [http://ubuntuforums.org/archive/index.php/t-33145.html](http://ubuntuforums.org/archive/index.php/t-33145.html) without success.  I tried both port numbers and added "@gmail.com" to my username (as well as without @gmail.com following my username).  No luck on any of the changes.

---

### Post by kmcavoy on 2009-05-04
What would happen if I uninstall and then re-install evolution?  I see that Synaptic Manager warns me that other programs depend upon this program.  Will I be in trouble or might it clean up the problem if it is missing something?  

Thanks for your advice,

Kerry

---


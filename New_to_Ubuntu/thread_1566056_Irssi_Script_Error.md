---
title: "Irssi Script Error"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by Information Overload on 2010-09-01
I'm new to both Irssi and Linux so I was wondering what it means when I get this error whilst trying to load some scripts in Irssi. 

I type in this:
/script load cap_sasl.pl

and I get this:

8:14 -!- Irssi: Error in script cap_sasl:
18:14 Can't locate Crypt/DH.pm in @INC (@INC contains: /home/connornickerson/.irssi/scripts /usr/share/irssi/scripts 
          /usr/lib/perl/5.10 /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 
          /usr/share/perl5 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at /usr/share/irssi/scripts/cap_sasl.pl line 237.
18:14 BEGIN failed--compilation aborted at /usr/share/irssi/scripts/cap_sasl.pl line 237.
18:14 

Can anyone decipher what this means I need to do? I was getting a similar error before: Can't locate Crypt::OpenSSL::Bigun. So I went and downloaded that code file off of the repository but I can't seem to find Crypt/DH.pm as a file in the repository. Could someone give me the location of this file and tell me where to install it? Or does the error mean for me to do something else? I'm confused at this point as I can't seem to find the answer on the internet.

---

### Post by jtarin on 2010-09-01
In your script "cap_sasl" there is a problem on line 237. It is possibly looking for something you don't have installed, or the script is calling for a non-standard location. It's Perl language, so you might have better luck re-posting in another forum, like programing and change the topic title to "Perl Script Problems in Irssi".

---

### Post by Information Overload on 2010-09-01
Okay I will do that, thanks.

---

### Post by andrew.46 on 2010-09-03
Hi Information,

I suspect that you are trying to use Freenode's sasl script? You are in fact missing a few perl modules, have a look at the following guide:

[Howto] Setup irssi and join #ubuntu on Freenode
[http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

and you will see that the SSL / sasl issues are well covered, including the relvant perl modules and ssl certs. Feel free to ask any questions in this thread, it is my guide and I actively support it :).

All the best,

Andrew

---


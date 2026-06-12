---
title: "Empathy MSN Problem"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by jzraikes on 2009-10-28
I just installed the Karmic RC and I'm having trouble connecting to MSN with Empathy. Whenever I try to connect I get an error message saying simply "Network Error". I am certain I am using the correct login information.
If it helps, I could connect to MSN with Pidgin, but only using 'HTTP Method', which Empathy doesn't appear to have.
I have a hunch that the cause of these problems may be something to do with my MSN address being "@fsmail.net" as opposed to "@hotmail.com" or "@hotmail.co.uk".
Any help would be appreciated. Thanks in advance.

---

### Post by sideffects on 2009-10-28
> **jzraikes said:**
> I just installed the Karmic RC and I'm having trouble connecting to MSN with Empathy. Whenever I try to connect I get an error message saying simply "Network Error". I am certain I am using the correct login information.
If it helps, I could connect to MSN with Pidgin, but only using 'HTTP Method', which Empathy doesn't appear to have.
I have a hunch that the cause of these problems may be something to do with my MSN address being "@fsmail.net" as opposed to "@hotmail.com" or "@hotmail.co.uk".
Any help would be appreciated. Thanks in advance.

Yeah, I was having some problems with Empathy as well. I still don't think it's ready to be the new default. My advice is to do like I did and install Pidgin.

---

### Post by jzraikes on 2009-10-28
> **sideffects said:**
> Yeah, I was having some problems with Empathy as well. I still don't think it's ready to be the new default. My advice is to do like I did and install Pidgin.
I've done so, but it would still be nice to not be stuck with Pidgin. I have same problem with aMSN as well...

---

### Post by avix on 2009-10-29
I need it for work for the video. same problem. [email]username@live.com[/email]. password, Advanced, server. Messenger.live.com port 1863. can import it from Pidgen (which works fine) but when imported into Empathy still get Network Error.

for the sever I have tried
messenger.live.com
messenger.hotmail.com
messenger.msn.com

---

### Post by CoreyB. on 2009-10-30
Same problem, Empathy won't connect my MSN accounts.  Using my default messenger.homail.com server and port 1863.

Any help?

---

### Post by avix on 2009-10-30
and this morning, they call came up fine, even MSN.. strange.

---

### Post by phasenew on 2009-11-11
installing python-msn solves.
sudo aptitude install python-msn

---

### Post by Paul Sinnett on 2009-11-12
I have this problem too and installing python-msn didn't solve it for me. There are some bugs being reported against this, [https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/471878](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/471878) and [https://bugzilla.gnome.org/show_bug.cgi?id=601359](https://bugzilla.gnome.org/show_bug.cgi?id=601359) and possibly others.

---

### Post by CoreyB. on 2009-11-13
python-msn did not solve it for me either.

---

### Post by LunaticHiatus on 2009-11-13
amsn works with webcam, but the best webcam support is via skype or ekiga. Works flawlessly yo

---

### Post by mlnease on 2009-11-18
I have the same problem in a recent fresh install of Karmic--python-msn didn't help me either.

---

### Post by arochester on 2009-11-18
I had this problem for several days.

I dual boot so I logged into Windows (When did I last do that?!). My MSN address was ***@yahoo.com. I updated Windows Live and got a Windows Live address ***@live.co.uk

Changed Pidgin account from MSN to WLM. Now works fine

---

### Post by RavanH on 2009-11-18
> **arochester said:**
> I had this problem for several days.

I dual boot so I logged into Windows (When did I last do that?!). My MSN address was ***@yahoo.com. I updated Windows Live and got a Windows Live address ***@live.co.uk

Changed Pidgin account from MSN to WLM. Now works fine

Could you explain what WLM is? I'd like to make my MSN account work on Empathy/Pidgin too. Thanks!

---

### Post by Hiperi0n on 2009-11-27
I have two msn accounts, my old hotmail account and a gmail account. If I log in with the hotmail account it empathy works. However, it doesn't with the gmail account.

---

### Post by foxy123 on 2009-11-27
The only solution to it is currently
```
killall telepathy-butterfly
```

Then put empathy offline and then make it available again.

---

### Post by Hiperi0n on 2009-12-05
Doesn't work. The telepathy-butterfly process is up just a few seconds while empathy trying to connect. Even killing it, empathy spawns it again. It will always give authentication error, no matter what...

In short, empathy works only with @hotmail MSN accounts...

---

### Post by arochester on 2009-12-05
> Could you explain what WLM is? Just read this A WEEK LATE!. The Microsoft Windows account used to be MSN (Microsoft Network)  - they are now calling their account WLM (Window Live Messenger). Pidgin has two accounts, either MSN or WLM...

---

### Post by Hiperi0n on 2009-12-05
I am using Pidgin 2.6.2 and only have MSN, not WLM. I thought it was the same...

Anyway, pidgin lets me log into MSN/WLM with my gmail account, whereas Empathy does not.

---

### Post by RavanH on 2009-12-07
> **Hiperi0n said:**
> Doesn't work. The telepathy-butterfly process is up just a few seconds while empathy trying to connect. Even killing it, empathy spawns it again. It will always give authentication error, no matter what...
Same here... However, what does work for me is to start up Pidgin first, let it connect and then close it again (not minimize to systray but complete close). After that, Empathy will connect my MSN account without problems! Funny...

> **Hiperi0n said:**
> In short, empathy works only with @hotmail MSN accounts...
Sadly, in my case it is a @hotmail old style MSN account :(

@arochester
Thanks for clearing the WLM mystery up for me :)

---

### Post by jviktor on 2009-12-11
> **foxy123 said:**
> The only solution to it is currently
```
killall telepathy-butterfly
```

Then put empathy offline and then make it available again.

I don't know how, but it worked for me, thanks a lot =D>

---

### Post by peacelake on 2009-12-21
> **arochester said:**
> I had this problem for several days.

I dual boot so I logged into Windows (When did I last do that?!). My MSN address was ***@yahoo.com. I updated Windows Live and got a Windows Live address ***@live.co.uk

Changed Pidgin account from MSN to WLM. Now works fine
Do you mean you registe a new live messange account and use it instead of using the old account? else how to do it, please explain.

---

### Post by Hiperi0n on 2010-01-13
I found the solution: 

[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9)

> 
ok try this remove telepathy-butterfly an you should just have telepathy-haze installed try connecting with that


I removed the telepathy-butterfly package and empathy now uses the telepathy-haze library to connect. It works with any account now.

---

### Post by RavanH on 2010-01-23
> **Hiperi0n said:**
> I found the solution: 

[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9)

I removed the telepathy-butterfly package and empathy now uses the telepathy-haze library to connect. It works with any account now.

Whooot! That did it :) 

Hiperi0n, THANKS for sharing that info!!!

---

### Post by d3v1150m471c on 2010-01-23
Use pidgin.

---

### Post by RavanH on 2010-01-25
> **d3v1150m471c said:**
> Use pidgin.
Yeah, but whatever I do, Pidgin always start with the Buddy List open. I hate that... Now with Empathy's MSN issue out of the way, it suits me just fine :)

---

### Post by gcs1984 on 2010-02-01
please delete this message.

---

### Post by DarkBattM14 on 2010-03-04
> **foxy123 said:**
> The only solution to it is currently
```
killall telepathy-butterfly
```Then put empathy offline and then make it available again.

oohh!!! THNX!!!! that worked for me!!!!! :popcorn:

---

### Post by conorsulli on 2010-03-04
> **Hiperi0n said:**
> I found the solution: 

[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9)



I removed the telepathy-butterfly package and empathy now uses the telepathy-haze library to connect. It works with any account now.

Works for me too!!!! Thanks

tip: Now under advanced the http method comes up as an option!

---

### Post by beemer2001ny on 2010-03-09
i'm using empathy 2.29.90 on 9.10.  I have no problems connecting to msn, icq, aim, yahoo.

I can't seem to get the msn video call to work.  when trying to place a call the video chat window comes up, my camera turns on, and I see myself.  However, the call never seems to get through to the other person.  They receive no indication a video call is trying to initiate.  Same is true when the other person using windows xp, windows live messenger trys to place a video, i get no indication a call is trying to be intiated.

Any help would be appreciated.  Thanks.

---

### Post by KcLKcL on 2010-03-13
> **conorsulli said:**
> Works for me too!!!! Thanks

tip: Now under advanced the http method comes up as an option!

This worked for me!

---

### Post by NilOGrav on 2010-04-12
I had the same problem as well, but reinstalling/restarting telepathy-butterfly didn't do the trick for me.

For me the solution was to have the complete account [email]user@hotmail.com[/email] in lowercase!? Bizarre since it is not case sensitive in the first place. I checked this by logging on to the hotmail website with various combinations of casing.


Hope this helps for some users.

Using empathy 2.30.0.1 on lucid beta.

---

### Post by fonsi2099 on 2010-04-14
My video option for MSN is still not working,  any idea? Thank you

---

### Post by paetsr on 2010-06-27
```
killall telepathy-butterfly

```

This worked for me as well. Don't know how it works but it does.

---

### Post by YannBuntu on 2010-07-03
@fonsi2099 : no video/audio calls for MSN protocol. Only with XMPP/Gtalk protocol as far as I know. (I recommand you use Telepathy PPA and install ubuntu-restricted-codecs if your interlocutors are on Windows Gtalk).

---

### Post by doooh_head on 2010-07-12
I tried this "killall telepathy-butterfly" command then put Empathy into offline mode.  Then I brought it all back online (set status to available) and msn came up successfully along with everything else.

It worked for me!

---

### Post by reyquito on 2010-07-12
> **Hiperi0n said:**
> I found the solution: 

[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9)

I removed the telepathy-butterfly package and empathy now uses the telepathy-haze library to connect. It works with any account now.

Thanks, that worked for me as well. However, something strange: before it connected the icon was in "busy", altough my status in other services was "available". I had to change status to "busy" for the connection to work.

Best regards.

---

### Post by repunante on 2010-09-15
> **foxy123 said:**
> The only solution to it is currently
```
killall telepathy-butterfly
```Then put empathy offline and then make it available again.


Yes, so far it worked for me as well, thanks!

---

### Post by BinaryEnCoder on 2010-09-22
> **paetsr said:**
> ```
killall telepathy-butterfly

```this worked for me as well. Don't know how it works but it does.
thanks man!!! It worked for me too

---

### Post by Beeblejj on 2010-11-13
> **BinaryEnCoder said:**
> thanks man!!! It worked for me too

Same

---

### Post by Beeblejj on 2010-11-13
> **BinaryEnCoder said:**
>  				 				**Re: Empathy MSN Problem** 			
  			  			 		   		 		 		  	Quote:
 	 	 		 			 				 					Originally Posted by **paetsr** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=9517613#post9517613") 				
 				[I] 	Code:
 	killall telepathy-butterfly 
this worked for me as well. Don't know how it works but it does.[/I]
 			 		 	 	 
thanks man!!! It worked for me too
  		                   		  		  		 		 			 				 

Same

---

### Post by bajeli on 2010-11-15
Same!!
Thanks

---

### Post by jack_the_lad on 2010-11-21
yeah, same here. thanks!:)

---

### Post by riky_6 on 2010-12-01
> **jviktor said:**
> I don't know how, but it worked for me, thanks a lot =D>

Me too :)

---

### Post by Digipete on 2010-12-01
<this worked for me as well. as a complete NOOb using the command line, can someone explain exactly what I just did? LOL
if i had to make an educated guess, from the bits i gathered, it closed part of the application..

---

### Post by catelee2u on 2011-01-28
Thanks very much - the python-msn worked for me

---

### Post by gnomeout on 2011-01-29
> **Hiperi0n said:**
> I found the solution: 

[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9)



I removed the telepathy-butterfly package and empathy now uses the telepathy-haze library to connect. It works with any account now.

This has solved my problem as well. It even provides the aforementioned "Http method" for connecting, although I did not need to use it, and I have a Gmail address for my Windows Live Messenger account.

---

### Post by leoismail on 2011-02-28
RIGHT OK EVERYONE LISTEN
I have no idea why, or wtf happened?
I just installed Ubuntu 10.10
It's some funky s***, I'm still coming to grips on how to use it, then I discovered the problems with the whole using empathy for facebook chat and windows live chat and tings.

looked at some forums and fixed fb chat, but managed to get windows live working

for FACEBOOK CHAT, you simply need to make sure you've created a username (not email address) login, you can do this in empathy, it says if you don't have a username click here blah blah blah ok.
MAKE SURE you then log into facebook using that username
empathy should then work.


Now...I'm sure you all know that anyway, it's on like loads of forums lol
but windows live

here's what i did

Firstly, whenever i used it, it just got stuck on connecting and never actually connected.

Then, i tried copying the port and server and put it into jabber, then logging in with that...didn't work
Did the same with google talk...didn't work

Then, for some retarded reason i accidentally changed the port like 3 numbers up
......IT WORKED

my port is set at 1866

I don't know why it works because I'm not a computer techie madman like a lot of you's are :)
But it just did.


I hope this helps guys, you know i just registered to this forum because i saw no one had a like....easy answer to it and i was like "OMGOMGOMGOMG TELL THEM!"

Muchos Loves

I'm really loving this whole Ubuntu shiz :D
so....shiny lol

---

### Post by TCattitude on 2011-04-21
> **Hiperi0n said:**
> I found the solution: 

[http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9](http://ubuntu-utah.ubuntuforums.org/showpost.php?p=8058121&postcount=9)



I removed the telepathy-butterfly package and empathy now uses the telepathy-haze library to connect. It works with any account now.

So far, so good.

Why this still asn't been solved yet?. Incredible.

But thanks for the tip ;)
Love Empathy gtalk audio-call support.

---

### Post by LordNodens on 2011-05-06
> **paetsr said:**
> ```
killall telepathy-butterfly

```This worked for me as well. Don't know how it works but it does.

Thanks a lot! It worked! (temporary fix)


Well, this actually solved the problem permanently:

Remove telepathy-butterfly and its dependencies.
 
sudo killall telepathy-butterfly
sudo dpkg --purge telepathy-butterfly
sudo apt-get install telepathy-haze

Reconfigure your MSN connections and attempt to activate them. You should experience no additional issues.

---

### Post by gabylastar on 2011-11-10
Removing telepathy-butterfly and installing telepathy-haze solved it for me. I had to remove the old account from Empathy and set up a new one.

The killall telepathy-butterfly method did not work.

---


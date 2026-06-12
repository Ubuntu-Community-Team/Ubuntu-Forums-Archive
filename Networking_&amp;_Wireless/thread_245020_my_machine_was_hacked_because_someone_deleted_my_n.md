---
title: "my machine was hacked because someone deleted my nicotine+ config"
date: 2006-08-27
forum: Networking &amp; Wireless
---

### Post by TOPPEL on 2006-08-27
all ports closed except 4 in the 60000 range.  i have ssh server as unchecked.  i have a very sensitive password to my machine.  only my ISP could know it.  i have AT&T DSL.  i am using a very good SOHO router.  i'm connected by wires.  my nicotine+ account was hacked while i was using it and that was another obscure password that also was not used anywhere else on the internet.   

thank you for your assistance.  

](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by TOPPEL on 2006-08-27
> **TOPPEL said:**
> all ports closed except 4 in the 60000 range.  i have ssh server as unchecked.  i have a very sensitive password to my machine.  only my ISP could know it.  i have AT&T DSL.  i am using a very good SOHO router.  i'm connected by wires.  my nicotine+ account was hacked while i was using and that was another obscure password.  

thank you for your assistance.  

](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

i know my machine was hacked because my nicotine+ config had been deleted.  that password is not used anywhere else on the internet.  

thanks !

---

### Post by OffHand on 2006-08-27
Do not make double posts please. Check your other thread for my reply.

---

### Post by TOPPEL on 2006-08-27
> **OffHand said:**
> Do not make double posts please. Check your other thread for my reply.

i prefer people post to this thread than the other i will instruct others to close the other thread.

---

### Post by TOPPEL on 2006-08-27
> **TOPPEL said:**
> i prefer people post to this thread than the other i will instruct others to close the other thread.

this is the thread i would like people to be focusing on.  i would like others to ignore the other thread.  thanks !  i will redirect them to this url.

---

### Post by OffHand on 2006-08-27
> **TOPPEL said:**
> i prefer people post to this thread than the other i will instruct others to close the other thread.

Whatever dude, I'm not gonna type it again though.

---

### Post by TOPPEL on 2006-08-27
> **OffHand said:**
> Whatever dude, I'm not gonna type it again though.

the only thing useful you told me was people could hack your machine through other apps not entry points.

all other ports were secured by my router.

---

### Post by OffHand on 2006-08-27
> **TOPPEL said:**
> the only thing useful you told me was people could hack your machine through other apps not entry points.

Ok, you probably arn't hacked but just lost you config file (cause unknown). If you still think you have been hacked change your password. Then install firestarter and configure nicotine+ and firestarter. Use the screenshots to get an idea of how to configure your ports with firestarter.

---

### Post by TOPPEL on 2006-08-27
> **OffHand said:**
> Ok, you probably arn't hacked but just lost you config file (cause unknown). If you still think you have been hacked change your password. Then install firestarter and configure nicotine+ and firestarter. Use the screenshots to get an idea of how to configure your ports with firestarter.

i got the notice "someone is logging in with your account and password" and then <disconnected>  both my system password and my nicotine+ password are obscure and unrepeated anywhere on the internet.  

it was hacked.  account and password changed.  

it happened when i first started using nicotine+ yesterday...

later in the day the config files were gone after reconfiguring the application completely.

---

### Post by OffHand on 2006-08-27
> **TOPPEL said:**
> i got the notice "someone is logging in with your account and password" and then <disconnected>  both my system password and my nicotine+ password are obscure and unrepeated anywhere on the internet.  

it was hacked.  account and password changed.  

it happened when i first started using nicotine+ yesterday...

later in the day the config files were gone after reconfiguring the application completely.

Like I said... change your password (both system and nicotine). Maybe you accidently shared your Nicotine folder with the conf file in it. Are you sure Nicotine isn't still running in the background?

---

### Post by Ivhassel on 2006-08-27
Your config files are in the directory : ~/.nicotine/
Your nicotine+ probably crashed, at that point your config gets reset to the defaults ( which makes you think it's deleted ).

Look at the file ~/.nicotine/config.old , open it with a text editor, and you'll see it contains all your stuff. close nicotine, rename the config.old to ~/.nicotine/config and restart nicotine+

should work again then.

---


---
title: "Cannot check hotmail, post on facebook, post on forums"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by RAZRBAKK on 2009-03-29
I am unable to post on forums, log into hotmail, post on facebook, and other things along those lines. I'm not sure what the issue is, but I NEED THESE THINGS!

Any ideas as to what I need to do to get this to work?

---

### Post by kanikilu on 2009-03-29
I don't suppose you could give any detail that might actually help us help you?

What browser? If Firefox, have you tried any other browsers (Opera, Midori, Seamonkey, Epiphany, etc...)?

Do you get any errors in the browser? Do you get any error messages if you start the browser from a terminal?

Is this a new install that has never worked, or was it working before and now not?

If it's just "all of a sudden" not working, have you tried creating a new browser profile (if using Firefox)?

---

### Post by RAZRBAKK on 2009-03-29
By the way, I'm using Sea Monkey and Firefox.

It will let me post on this forum, for some reason...

---

### Post by RAZRBAKK on 2009-03-29
Bump.

---

### Post by Ugluk on 2009-03-29
Is there some error message, in those forums' login/post interface? What exactly happening when you're trying to post?

---

### Post by mali2297 on 2009-03-29
Just an idea... Look through the preferences of the browser. Check that you have javascript and java enabled and that you allow cookies.

---

### Post by RAZRBAKK on 2009-03-29
> **Ugluk said:**
> Is there some error message, in those forums' login/post interface? What exactly happening when you're trying to post?


I get this when trying to get onto hotmail

> Connection Interrupted

      

      
      
      

      
        
        

          

The connection to the server was reset while the page was loading.

        


        
        

The network link was interrupted while negotiating a connection. Please try again.

On Facebook and other forums, it will just keep loading, forever.

---

### Post by alfplayer on 2009-03-30
I'm on ADSL and I was having a similar issue (Facebook, Hotmail would appear badly formatted and the page load would not complete). I solved the issue by setting the MTU parameter of the network interfaces to 1492, it is set by default to 1500. I think it is a limitation of ADSL.

---

### Post by LowSky on 2009-03-30
You shouldnt have any issues getting onto facbook or this site. I know hotmail has been an issue for some but I think there was trying to use it from tunderbird or something.

Most likely you have an issue with you network. What kind of connection do you have>?

---

### Post by RAZRBAKK on 2009-04-01
I have a wireless connection.

It all worked fine last night, but this morning, upon restart, I cannot connect once again. I don't believe anything has changed.

---

### Post by billgoldberg on 2009-04-01
> **RAZRBAKK said:**
> I have a wireless connection.

It all worked fine last night, but this morning, upon restart, I cannot connect once again. I don't believe anything has changed.

It sounds like a bad wireless connection.

Try finding out what channels the wireless networks in your area or on (the ones you can see in network manager).

You can find out with aircrack-ng.

```
sudo apt-get install aircrack-ng
```

Then get your wireless card into monitor mode 

```
sudo airmon-ng start wlan0
```

Then scan the wireless networks in your area.

```
airodump-ng mon0
```

And look at the channels your neighbors are using.

Then change the channel of your wireless network to one that isn't being used by them.

This must be done in the routers interface.

Open firefox and go to [http://192.168.1.1](http://192.168.1.1) (could be different) and look around for it.

Changing channels can give an big boost in your wireless networks performance.

note: wlan0 and mon0 could be different on your pc. use iwconfig to see what interface you are using.

edit: don't worry if the aircrack-ng stuff doesn't work. Not every card has monitor support OOTB, some don't even support it at all. Just changing the channel in the router will most likely work.

---

### Post by Yashiro on 2009-04-01
Disable your plugins. It sounds like you've just installed noscript.

---

### Post by Dougie187 on 2009-04-01
I know this doesn't help much but I don't think anyone NEEDS facebook.

---

### Post by Yashiro on 2009-04-01
You must be an old man like me. :P
Facebook IS the internet for people under 25 these days.

---

### Post by billgoldberg on 2009-04-01
> **Yashiro said:**
> You must be an old man like me. :P
Facebook IS the internet for people under 25 these days.

No it isn't.

But this isn't the Cafe guys, keep it on topic.

---

### Post by Yashiro on 2009-04-01
Trying out for moderator, eh? Good job, keep it up.

If he can browse but not post it's more likely a client side issue than his connection.
Hence the OP should try another browser that is not mozilla, or double check all his plugins.

If he is 100% sure absolutely nothing has changed then try a full power cycle of all equipment then repost.

---

### Post by Dougie187 on 2009-04-01
> **billgoldberg said:**
> No it isn't.

But this isn't the Cafe guys, keep it on topic.

With the pink its hard to tell.

Either way, it just sounds like he has a crappy connection.

Maybe he could try hardlining his comp and seeing it that works. Then you could be sure it was his wifi.

---

### Post by billgoldberg on 2009-04-01
> **Yashiro said:**
> Trying out for moderator, eh? Good job, keep it up.


No.

Let's see how you like it when you have problems and all the posts are off topic babble.

To OP:

Did the changing of the channels help?

Some feedback would be helpful.

---

### Post by alfplayer on 2009-04-01
You should try other browsers.

You can try changing the MTU. Here you have a simple how to: [http://monespaceperso.org/blog-en/2009/02/26/how-to-change-the-default-mtu-of-a-network-card-on-ubuntu/](http://monespaceperso.org/blog-en/2009/02/26/how-to-change-the-default-mtu-of-a-network-card-on-ubuntu/)

The tutorial uses eth0 as the name of the network interface, you need to replace it with the name of your wireless interface (sometimes it is wlan0). If you don't know it you can find it out by running:
```
iwconfig
```It is not risky if you do it right. Later you can try different MTU values (leave it as higher as possible to have the fastest connection).

---

### Post by RAZRBAKK on 2009-04-01
Changing the MTU seems to have worked. All the stuff is functioning again.


Hooray!

Thanks guys.

---

### Post by Yashiro on 2009-04-01
Prize goes to alfplayer. :)

---

### Post by RAZRBAKK on 2009-04-01
*Facepalm*

Nevermind.

---

### Post by CRIMPS on 2009-04-01
Conficker!  Yeah, thats it!
:lolflag:

---

### Post by CRIMPS on 2009-04-01
> **CRIMPS said:**
> Conficker!  Yeah, thats it!
:lolflag:

Sorry, that wasn't very helpful :(

---


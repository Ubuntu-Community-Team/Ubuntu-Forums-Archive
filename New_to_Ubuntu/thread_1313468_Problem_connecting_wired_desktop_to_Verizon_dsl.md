---
title: "Problem connecting wired desktop to Verizon dsl"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by mjp29 on 2009-11-03
My mother and I both use Verizon dsl internet.  I put Ubuntu 9.10 on a desktop box to give her.  I connected the ethernet cable to the computer at my home and it instantly recognized and went on the internet without being configured.  I even set up her Thunderbird email account using her email password from my home.  It worked to.  She lives 2.5 hours away from me by car travel.  My wife was in her town on official work business today and delivered the computer to her.

Now, she plugs the computer in via ethernet cable to her Verizon dsl modem box and it will not automatically go onto the internet.  At my home, I think it was automatically going on the net with wired VPN connection which was Auto Eht0 wired connection.  Hers will use that as it is still setup the way I sent it to her.

In VPN connections, then click configure VPN, we even tried deleting the Auto Eth0 under the "wired" tab.  Then we clicked on the "DSL" tab and added a dsl connection.  In the menu that appeared we seen that it put "Connection name:  DSL connection1" and we checked connect automatically (which is what it was doing at my house but I think it was doing it under the wired tab).  Under where we checked "connect automatically" we didn't feel that we needed to type in what was below that and applied and tried it.  It didn't work.  We then went back to the "DSL connection1" and entered her usnername (her verizon username which is her first few characters in her email before the @verizon.net).  We entered "Verizon" in the Service field.  We entered her email account passowrd in the "Password" field.  We left the box below which is "show password" blank.  It still wouldn't connect.

Frustrated I am and she is.  I thought since we both used Verizon and it connected automatically to my Verizon modem box when the ethernet cable was plugged in that it would do the same at her house.  But no it did not.  I believe we do both have different Verizon dsl boxes as mine is wireless and I don't think hers is.

Please please someone help.  I'm trying to get a senior citizen here to use Ubuntu because she really liked it's interface at my home and wanted it so bad she went out and bought a new 22" HP monitor and wireless HP mouse.  Please help this poor soul connect to the internet on Ubuntu (LOL in a way but not really funny - LOL anyways).

---

### Post by wrgb2 on 2009-11-03
VPN connections shouldn't have anything to do with it -- plugging the ethernet cable in should get her on the internet if the modem/router is set up correctly.  Is there a link light on the Ethernet card and the modem?  If so, try opening a browser and typing in the address field [http://192.168.1.1](http://192.168.1.1) . This should bring up a menu and somewhere she can put her username and password in.  You may need to set the router to bridge mode, but I don't think so.  Hope this helps.

---

### Post by mjp29 on 2009-11-04
> **wrgb2 said:**
> VPN connections shouldn't have anything to do with it -- plugging the ethernet cable in should get her on the internet if the modem/router is set up correctly.  Is there a link light on the Ethernet card and the modem?  If so, try opening a browser and typing in the address field [http://192.168.1.1](http://192.168.1.1) . This should bring up a menu and somewhere she can put her username and password in.  You may need to set the router to bridge mode, but I don't think so.  Hope this helps.


just to clarify, a "link light" means that the ethernet cable from the computer is being recognized by a l.e.d. light where the ethernet cable is plugged in from the computer, right?

---

### Post by wrgb2 on 2009-11-04
Correct.  The link light basically means that the ethernet card and the router are working ok and that the cable is good.  The link light may be labeled "Ethernet" on the modem and it will be near the Ethernet jack on the network card.

---

### Post by NickJones on 2009-11-04
Does it show it as being connected?

---

### Post by mjp29 on 2009-11-04
> **wrgb2 said:**
> Correct.  The link light basically means that the ethernet card and the router are working ok and that the cable is good.  The link light may be labeled "Ethernet" on the modem and it will be near the Ethernet jack on the network card.


We just tested this and the light does come on the Verizon Westell model number D90-327W15-06

She unplugged the ethernet cord and a the light went on.  She plugged the ethernet back into the Verizon router and the light came back on.

So this is good news, right?

---

### Post by wrgb2 on 2009-11-05
Yes, that's a good thing.  Now have her open Firefox and type in the address bar [http://192.168.1.1](http://192.168.1.1)   This will open a menu for the modem.  Somewhere in that menu is a place for her to enter her username and password.  Once that's done, turn the modem off and back on again, wait a bit and she should be able to connect to the Internet.  Note: If the router is new and was not being used with another pc before ubuntu, it may need additional setup -- she'll have to call verizon for the information needed to do that

---

### Post by mjp29 on 2009-11-05
> **wrgb2 said:**
> Yes, that's a good thing.  Now have her open Firefox and type in the address bar [http://192.168.1.1](http://192.168.1.1)   This will open a menu for the modem.  Somewhere in that menu is a place for her to enter her username and password.  Once that's done, turn the modem off and back on again, wait a bit and she should be able to connect to the Internet.  Note: If the router is new and was not being used with another pc before ubuntu, it may need additional setup -- she'll have to call verizon for the information needed to do that

If you want to skip over the rambling I've done below and go straight to what this forum needs to read and reply to then please scroll down to "With all that said, we are at this point." and read that below.  Otherwise you will be reading things below that will be verging into an area of insanity.

ok, please understand that I am doing this with my mother that is so computer illiterate that the other day when I told her to look at the top right and find her name to then select shut down or restart, that she was actually [and this is no joke but very funny], she was actually looking at the top right of the actual computer box (the dell box) to find shut down or restart on the actual cpu hardware box.  People out here on the forum have no idea how computer illiterate she is and how frustrating it is to me to try to help her get her system online from 2.5 hours away.  It almost drives me to a point of insanity.  But she really likes Ubuntu, as she came to my home and seen it and used it and REALLY likes it, so I have committed myself to help ANYONE get Ubuntu to work on their box if they want Ubuntu - even my completely computer illiterate mother [LOL].


With that said, this is the step we are at.

She has opened Firefox [even though some Verizon screen keeps popping up which I'm not sure it's coming from within Firefox or from the Ubuntu operating system because she chose dsl in vpn connections - I know it's not coming from the internet as she is not on the net yet; HOWEVER I can't be sure it didn't get delivered to her on the net as she has indicated to me (time and time again that I wrote all the details down and we tried to allow the veriozn box that appears to set up her dsl - and I can actually post every little detail here what the Verizon box says if that will help) that during brief periods of time something on her Ubuntu box tells her she is connected to the internet.  When she tells me that I tell her to quickly go to Firefox browser and type in [www.google.com](www.google.com) or another website like [www.apple.com](www.apple.com) to see if the internet is allowing her on and allowing her to go to websites - but it won't.  The only site she ever gets is when she initially opens Firefox the default Ubuntu site comes up but I personally believe that is built into the operating system and she isn't acutally connected via internet to the Ubuntu website.  

With all that said, we are at this point.
She opened Firefox.  I told her to make the Verizon box go away hoewever she needed to (X-ing it out, quitting it, whatever and open Firefox so that you don't see anything Verizon on your scree).
She typed in the [http://192.168.1.1](http://192.168.1.1) and she says she sees on her screen at the bottom of the Mozilla Firefox big box she says whatever you call it the big box that opens up.  She says she thinks this is showing up at the bottom of the browser [firefox] because at the very very bottom of her screen she only sees "update manager" and another box that says "Westell versalink wire..."   She says at the top of the browser [firefox] says "Loading" and it has a circle spiraling and the circle keeps spiraling around and around and around, and she has waiting 15 minutes watching this circle spiral.

I would go on and tell her to turn the modem off and back on again, wait a bit and tell her then she should be able to connect to the internet.  However, I want to give you guys/gals here on the forum a chance to tell me if I should immediately tell her to do that as I think her cpu is trying to load onto the internet and I don't want to tell her to do the next step if the cpu needs time to set ups its connection to the net.

In a nutshell, should I tell her to quit Firefox browser now and then turn modem off a bit, and proceed to turn modem back on and then go to Firefox and attempt to go to a webpage like [www.google.com](www.google.com)  Should she need to restart her Ubuntu box at any time?

waiting

modem secure

---

### Post by wrgb2 on 2009-11-05
Are you still there?

---

### Post by mjp29 on 2009-11-05
> **wrgb2 said:**
> Are you still there?

yes

---

### Post by wrgb2 on 2009-11-05
do you have an im account?

---

### Post by mjp29 on 2009-11-05
i have snype account or something

but please email me in my user cp account (my email is available).  and I will give you my phone number and my mothers phone number to call.  do you live in north america, if so you could give us your phone number and we'll call you and it will only be billed to us (personally, i have verizon phone package where i'm paying to be able to call anyone in north america without being charged by the minute).

---

### Post by mjp29 on 2009-11-05
i am curious

i am considering buying the Canocial support to get this resolved.

do you know how much it costs and if they would cover this type of issue [i know on the ubuntu website they said on the record they support only installation support - which we've already installed ubuntu, does that or does not installation support cover support for getting my poor mother connected to the internet?

regardless, if you and i or you and mother can be put in contact with each other some way on the phone [trust me, trying to IM mother will frustrate the hell out of you] then I'd much prefer to speak with you by voice or you speak with her via voice to fix this problem.

thanks so much to you for your kinda help

---

### Post by mjp29 on 2009-11-11
This problem was solved below.  I want to thank wrgb2 for calling me and my mother/sister to help resolve this problem.  Below, you will see the solution.  Below, also, is actually a copy and paste to a private message I sent to wrgb2.  Marking this thread solved.  The lesson and moral of this story is don't ever allow anyone (be it Verizon, Suddenlink, Linksys, etc...) tell you they won't help you because you are using Linux and they don't support it.  If you get in contact with the right person (at Verizon, Suddenlin, Linksys, etc...) you can get good help.  How do I know?  Because my uncle is using a Linksys wireless setup at home and couldn't get his Ubuntu to work with his wireless Linksys hardware.  My Uncle was first told on the phone they don't support Linux and only help people that have Windows or Mac.  I called back and rose a little hell and was connected with a person that told me without a doubt that Linksys would help me solve the problem and that indeed without a doubt we could use Ubuntu linux with their wireless hardware and make it work.  

I switched out the Ubuntu computer mom had with another Ubuntu computer I had at home - we met half way.

That Ubuntu computer also didn't work.  So I eliminated the variable that it was the computer.

I called Verizon and raised a little hell and although they had told mom and my sister that they only supported Windows and Mac, the person I raised a little hell with told me there was a special 1800 number for Verizon that supports Linux installs.

I called the special number and these people at Verizon actually understood the problem.  They said it was the router.  They put me on a 3 way call with my mom/sister and solved the problem using Firefox browser to reprogram (reconfigure) mom's Verizon router.

Bam - it worked!

Mom is so happy now.

Just wanted to share that with you.


mp

---


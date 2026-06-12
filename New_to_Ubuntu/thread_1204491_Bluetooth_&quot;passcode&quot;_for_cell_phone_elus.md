---
title: "Bluetooth &quot;passcode&quot; for cell phone elusive !"
date: 2009-07-04
forum: New to Ubuntu
---

### Post by faron45 on 2009-07-04
Trying to reply to someone who replied to a post of mine a while back [2 months ago ?] with the user name "987poiuytrewq" I wrote.....

987poiuytrewq-Have purchased the adaptor...HUGE PROBLEM though.....phone recognizes my pc.But,phone wants a "passcode" & I have absolutely no idea what this is & trust me,I have been trying to find out.I have read several blogs about this.I have tried 0000,00000,1234,123.No luck though.

Then...I read... "Also, is it possible that your BT adapter came with a code already programmed into it, and now you need to match that code?" IF this is the case...ohhhhhhhhhh my God ! How do I find out what this code is ????? Ahhhhhhhhhhhh !! Helllllllllpppppppppppppp............. PLEASE !!!!!!!!!!!!!!!! PRETTY PLEASE !!!!!!!!!!!!!!!!!!! 

Tracfone says the only way to transfer pics with this phone to my pc is by using my airtime mins !! BUT...I have read other blogs stating indeed that that is not the case.

---

### Post by niteshifter on 2009-07-04
Hi,

Bluetooth is simple. So simple it's tricky. Very tricky at times.


A phone wanting a passcode? It wants the passcode for the computer. The below should reveal it:
```
cat /etc/bluetooth/hcid.conf | grep passkey
```
The above is for Bluetooth on the computer provided by the bluez package. Search in Synaptic for 'bluez', if it's installed the above should work.

However I have seen phones that ask for a passcode - when the phone wants to set a passcode. Even when initiating the "pairing" from the phone-end of the link. This is followed by the computer popping a dialog also asking for the passcode. Enter same both places.

I think your's is the first case.

FYI - Tracfone may be right. The forums you read may also be right. I'm not familiar with Tracfone, but it does happen that a cell provider has certain phone features locked out, forcing users to transfer media files over their network. 
The solution is to "mod" the phone. Risky - you better know what you're doing or you'll brick the device. Many forums are around dedicated to modding phones. This may have been what you've read about.

---

### Post by faron45 on 2009-07-04
Niteshifter.thank you very much.Sorry it took me awhile to reply..my daughter came by & I don't get to see her often.Unfortunately,we have been estranged.But,I will try what you have suggested......And,as far as the phone being "locked" that could indeed be the case but,I don't think so.None of the posts I have read have said anything about that.[hopefully].I'll let you know what happens later.Again,THANK YOU VERY,VERY MUCH.

---

### Post by Dougie187 on 2009-07-04
If it was pre-programmed and options like 1234 and 0000 don't work, you could always try the last 4 of your phone number.

---

### Post by faron45 on 2009-07-04
Nothing seems to be working.It would seem that I am indeed locked out.Well,it doesn't look like I'm going to be a Tracfone customer very much longer.

---

### Post by faron45 on 2009-07-04
It would seem also that they may be getting ready to "brick" me over as the gentleman said earlier.I've gone into my phones pre paid menu & the # that it is now showing for my phone is not the number that I was assinged.Although,so far,I am still able to make & recieve calls.

Thought maybe I should also mention that when I attempt to try any of these things it is only the phone that is asking for a code.The pc never asks.

---

### Post by niteshifter on 2009-07-05
@faron45:

Got your message, responding public so all can benefit ...

About how to mod your phone: Honestly, the best advice I can give is to google for it - phone make, model, and the word "modding". Example for a Motorola V3xx:
```
motorola V3 modding
```
Put into google, see what you get. Cross check information and "howto" procedures on any site you find with other sites.

Study up and be very careful should you decide to mod your phone as you'll be changing the deep internals (firmware) of how that computer (your phone) works. One mis-step, a power glitch (weak battery), crappy homebrew mod software and the phone can become completely useless.

---


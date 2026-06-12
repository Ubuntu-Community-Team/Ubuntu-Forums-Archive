---
title: "Ubuntu One Files - the android app"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by CaptainMark on 2011-07-22
Has anyone used the Android app for ubuntu one file sync, I think its awesome and really useful to link my desktop and my phone but since installing it absolutely murders the battery, I've got an HTC desire which is not very battery friendly to start with but since installing it I can barely make it through an average days use without a full charge being completely used up. If anyone has this phone or similar download the app from the market and let me know what you think.

---

### Post by kaspar_silas on 2011-07-22
Yip I had the same problem. A stock desire under absolutely any load just eats battery. Lasting about a day is alas about par for the course. It's a real pity as apart from that it's a truly great phone.

You can improve it slightly by rooting it and massively reducing the CPU upper limit.

---

### Post by CaptainMark on 2011-07-22
its a shame im going to have to unistall this app until it get a lower power footprint, its a great app but i have to really minimise even touching it throughout the day to reach dinner time and if im going out in the evening straight after work i have to disconnect the mobile internet at about lunchtime to stand half a chance of making it past midnight with any battery left, theres no point having a phone if i cant use it at all

---

### Post by philinux on 2011-07-22
The work around for me is to use the HD's browser to access ubuntu one website to access or upload files.

---

### Post by CaptainMark on 2011-07-22
more of a totally different method than a work-around,
ill try setting the photo sync to hourly or twice-daily instead of instantly see how that goes for a few days first before i completely trash it

---

### Post by gandaran on 2011-07-23
I would like to try the Ubuntu One Files app on my galaxy android phone but the app fails to connect (it doesn't even asks for username and password) so how do you use it or set it up?
thanks

---

### Post by CaptainMark on 2011-07-23
it should just start up on a page offering to login or sign up. try  deleting the cache and data files for it, settings>applications>manage applications>all>ubuntu one.
ive definitely noticed a huge improvement in battery usage when reducing the photo autosync to hourly, ill try bring it right down maybe daily and i think it can stay for now

---

### Post by gandaran on 2011-07-23
> **CaptainMark said:**
> it should just start up on a page offering to login or sign up. try  deleting the cache and data files for it, settings>applications>manage applications>all>ubuntu one.
ive definitely noticed a huge improvement in battery usage when reducing the photo autosync to hourly, ill try bring it right down maybe daily and i think it can stay for now
hi
if I click on login button the app tries to connect but just fails and clicking on the register button I can login from the internet browser but even after login to Ubuntu one webpage the app still won't work.
maybe the app doesn't work with Froyo 2.2!

---

### Post by CaptainMark on 2011-07-23
i have 2.2 as well, sign into another ubuntu single sign on site (these forums or launchpad) and see if the server picks up the connection automatically

---

### Post by mkarnicki on 2011-07-26
Hi everyone,

I'm lead developer on Ubuntu One Files. Let me answer few of your questions / thoughts.

First of all, thank you for your kind words, we're doing our best to make the app rock.

As far as the issues are concerned:

@CaptainMark Switching to periodic upload instread of "instant upload" is buggy. It works, but only temporarily. We will have this fixed in following update. (patch is already proposed). If you use instant upload, it is Android which keeps Wi-Fi ON (in case Wi-Fi connection was used) for next 15 minutes even if you don't use it. It's system policy. Using either Mobile connection or periodic sync (like every 6 hours) should have positive impact on the battery life.

"it should just start up on a page offering to login or sign up." - it will :)

@kaspar_silas "A stock desire under absolutely any load just eats battery" - thank you for response, it's imporant for me to know these things as well

@gandaran "Login failed" is caused by wrong time settings. Once switched to 'Automatic' under Phone > Menu > Date & time, you should be able to lauch the browser to authorize the app.

Some users reported issues with Opera. Please use your system default browser to authorize the application. Otherwise, (just like Opera, also depending on the version) the browser may have problems redirecting back to the application.

As far as last CaptainMark's suggestion, that won't work. Please make sure to sync time and use the default browser (I think FF works as well).

---

### Post by gandaran on 2011-07-26
> @gandaran "Login failed" is caused by wrong time settings. Once switched to 'Automatic' under Phone > Menu > Date & time, you should be able to lauch the browser to authorize the app.
mkarnicki
hi
thanks for the reply
I did finally read about this in the ubuntu one apps market description and enabled automatic time then tried connecting I think two times and the same fail message came up so I just removed the app, maybe I was impatient or something, probably should have rebooted the android system first! I'll try re-installing the app again.

---

### Post by CaptainMark on 2011-07-26
its a good app that will be even better once the few bugs are ironed out, however with regards to the battery consumption i never leave wifi on, infact i rarely turn it on at all but just having the sync set to instantly with mobile internet still just seems to absolutely kill the battery, if i have it set to instantly i get about 16 hours tops under normal use if i turn off autosync (as you mention the periodic setting does not stay set) i can get about 48 hours (no other settings changed, and no wifi at all)

---

### Post by gandaran on 2011-07-27
nope, even with automatic time enabled the Ubuntu one app still doesn't connect, looks like automatic time is not working on my Galaxy Ace with Froyo 2.2, I don't know why, maybe it's because I don't have a 3g internet plan I only connect to internet using wi-fi network and the only way to get the right time display on my android is to set it to a GMT-00:00 time line.
I'm really disappointed it doesn't work here.

---

### Post by mkarnicki on 2011-11-08
@gandaran

Really sorry to hear about that. Have you tried the app since then?

Also, you made an interesting point (as we still have some users with this issue):

"and the only way to get the right time display on my android is to set it to a GMT-00:00 time line."

You mean you won't get the right time if you set it to your timezone (whatever the timezone it is) ?

---


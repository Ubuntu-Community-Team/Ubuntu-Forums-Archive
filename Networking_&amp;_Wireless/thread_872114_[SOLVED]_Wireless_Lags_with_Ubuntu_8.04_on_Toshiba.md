---
title: "[SOLVED] Wireless Lags with Ubuntu 8.04 on Toshiba Laptop"
date: 2008-07-27
forum: Networking &amp; Wireless
---

### Post by cybrsaylr on 2008-07-27
With the help of this forum I got my wireless Belkin (My Essentials ME 1004-R) router to connect with my new Toshiba laptop. My laptop is a dual setup with Vista/Ubuntu. When on Vista everything loads fast but when switching to Ubuntu the wireless works but loads pages very slowly most of the time. When hardwired both Ubuntu and Vista load very fast. It is only when using the wireless router on Ubuntu that this slowdown happens. I called the Belkin 'helpline' and they had no clue why it slows dowm on Hardy but not on Vista. They claim it should run just as fast on both OSs. 
Anyone have any ideas on how to speed things up here?

---

### Post by cybrsaylr on 2008-07-30
Got a hold of a wireless G Belkin USB Network Adapter hoping it would help. Plugged it into a USB port and Hardy recogized and connected to it as an extra wireless network with a stronger reading than before, it now hits 100% while before it only hit 90-92 at best in spite of being <5 feet from the router. 
However it still loads the first page of a site slow, then speeds up some once into any site selected. Anyone have any ideas how to gets rid of the lag? As I said when the laptop is hardwired it loads all sites and pages very fast but when going wireless there is this annoying lag.

---

### Post by cybrsaylr on 2008-08-02
Bump.


Anyone have any ideas on speeding things up here?

---

### Post by jualin on 2008-08-02
IPv6 issue maybe? Type > about:config on your Firefox address bar, and perform a search for "IPV6" then toggle the state from "false" to "true". That seems to be the problems sometimes.

---

### Post by cybrsaylr on 2008-08-02
> **jualin said:**
> IPv6 issue maybe? Type  on your Firefox address bar, and perform a search for "IPV6" then toggle the state from "false" to "true". That seems to be the problems sometimes.

I did that in FF and could not find any IPV6.

This is the last entry before going to Js:

intl.menuitems.insertseparatorbeforeaccesskeys;  default    string  true

---

### Post by jualin on 2008-08-02
What version of firefox are you running?

---

### Post by cybrsaylr on 2008-08-02
I have FF 3.0.1. but use Opera all the time.
I prefer Opera to FF.

---

### Post by jualin on 2008-08-02
I am running Firefox 3.0 and mine says "network.dns.disableIPv6". You can do a search with that and you will find it.

---

### Post by jualin on 2008-08-02
[This link is for OpenSuse]("http://en.opensuse.org/Disable_IPv6_for_Firefox") but it's the same in any Firefox as far as I know.

---

### Post by cybrsaylr on 2008-08-02
> **jualin said:**
> I am running Firefox 3.0 and mine says "network.dns.disableIPv6". You can do a search with that and you will find it.

Found it, it says:

network.dns.disableIPv6; default   boolean   false

---

### Post by jualin on 2008-08-02
Now toggle it to "true"

---

### Post by cybrsaylr on 2008-08-02
> **jualin said:**
> Now toggle it to "true"

OK I did that, then rebooted to wireless and FF seems much faster than before but Opera, my favorite browser, still has lag.
 I Wonder if there is a similar setting to change in Opera also to speed things up?

---

### Post by jualin on 2008-08-02
Ok, let me check. I am pretty sure there is.

---

### Post by jualin on 2008-08-02
What I suggest is disabling IPv6 globally. [In this post]("http://ubuntuforums.org/showpost.php?p=4891172&postcount=2") they explain how to perform that. Remember don't forget to reboot after you make the change. Tell me how that goes.

---

### Post by jualin on 2008-08-02
Be careful because on his post he says > 3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off. meaning that you are going to take out the **ipv6** part and replace it with **off**. I know it sounds dumb but my friend actually thought that when someone says write "alias" without the quotes they meant write **"alias" without the quotes** instead of just **alias**. :lolflag:

---

### Post by cybrsaylr on 2008-08-02
> **jualin said:**
> Be careful because on his post he says  meaning that you are going to take out the **ipv6** part and replace it with **off**.

OK, did it and Opera seems to be flying again almost like it's hardwired.
I think that did the trick.
Thanks jualin for the help....):P

---

### Post by jualin on 2008-08-02
Anytime dude. Glad it worked. I hope his also works for the person who created the other post. Also remember to mark the thread as solved please. Thank you in advance and Greetings from Miami, FL

---

### Post by cybrsaylr on 2008-08-03
OK.
Just marked it solved and Greetings from NY...;)

---

### Post by cybrsaylr on 2008-08-22
FWIW

Just thought I'd report back that I applied this same fix to my desktop and it worked on the desktop also. What was happening was while hardwired my desktop was very fast using both FF and Opera. Then I bought a laptop and a wireless router. After setting up the router the desktop slowed down and to some extent so did my new laptop. This 'fix' on  ipv6 sped up the laptop on both FF & Opera but now the desktop lagged unless I shut the router down and hardwired it again. So I thought I'd give this a 'fix' a try on the desktop and now it is a lot faster again with the router on and the lag seem to be gone.

While the new dual core laptop is only a few months old the desktop is over 11 years old (Pent II) and I thought it had seem its day. However now it's flying again and may have a few more days in it before it goes to the boneyard.

---

### Post by cybrsaylr on 2008-09-20
Been playing around with OpenSuse 11.0 and had this lag there also.

I followed the directions for Firefox3 to fix the IPv6 lag and it worked. FF is now quicker however Opera still crawls. Tried the fix posted above in Terminal but it won't work in OpenSuse Terminal like it does in Ubuntu Terminal.

Does anyone have to correct OpenSuse command that will fix this IPv6 issue in OpenSuse like it did for Ubuntu?

---

### Post by jualin on 2008-09-20
I found this [link]("http://en.opensuse.org/SDB:Disabling_IPv6_completely") online. Maybe it will help you. However I can't confirm it since I am not using OpenSuse.

---


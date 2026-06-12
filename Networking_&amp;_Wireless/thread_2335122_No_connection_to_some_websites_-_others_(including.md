---
title: "No connection to some websites - others (including this one) works"
date: 2016-08-25
forum: Networking &amp; Wireless
---

### Post by Jerriy on 2016-08-25
So far I'm only able to  make out that it's def. not a browser, firewall or wifi network issue.

16.04's inbult help (F1) has nothing whatsoever on offer. The only  troubleshoot in my help section is related to wifi, which is perfectly fine in  my case (otherwise I wouldn't be making this message).

---

### Post by TheFu on 2016-08-25
Network troubleshooting ... [http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking)
Hope that helps.

Usually when a few sites don't work, but a few others do, it is an ISP network connection issue. Time to start monitoring the internet connection and DNS.  A failed DNS can appear as "the internet is broke" to non-technical people.

---

### Post by Jerriy on 2016-08-25
@TheFu - I can't connect to that site (jdpfu.com) evidently one of the blocked ones.

And one more thing: some sites are half-connected (for example I can access some yahoo pages while I can't others.

> **TheFu said:**
> A failed DNS can appear as "the internet is broke" to non-technical people.I am one of those people.

I need exact terminal instructions. 

My technical knowledge is limited to typing "host" before a site and discovering the IP numbers. In this case typing those in the browser didn’t' solve the problem.

---

### Post by TheFu on 2016-08-25
> **Jerriy said:**
> @TheFu - I can't connect to that site (jdpfu.com) evidently one of the blocked ones.

Try a different browser?
Google cache?
Wayback machine?

Some countries have decided to block that website for unknown reasons. Some ISPs are forced to implement the will of the country leadership. Everything on it is PG rated and non-offensive towards **any** specific group, country, etc.   IMHO. If you are in one of those countries with large internet filters, then I think we have **the reason** why some websites are blocked.  I vaguely recall that wikipedia has an article about which countries do internet filtering.

---

### Post by Jerriy on 2016-08-25
No it has nothing to do with any of that because I did have access to those sites yesterday.

Nothing happened overnight that caused half websites to shut down here.

Now I did a ping and the result was "destination Port Unreachable"

---

### Post by TheFu on 2016-08-25
Go by IP, not DNS name.

---

### Post by Jerriy on 2016-08-25
I have no idea what you mean.

Whatever banned IP I ping I get "destination port unreachable"

---

### Post by SeijiSensei on 2016-08-25
[www.google.com](www.google.com) has address 173.194.219.99
[www.google.com](www.google.com) has address 173.194.219.103
[www.google.com](www.google.com) has address 173.194.219.104
[www.google.com](www.google.com) has address 173.194.219.105
[www.google.com](www.google.com) has address 173.194.219.106
[www.google.com](www.google.com) has address 173.194.219.147

Can you see [http://173.194.219.99/](http://173.194.219.99/) or one of the other addresses above?

---

### Post by Skaperen on 2016-08-25
> **Jerriy said:**
> Now I did a ping and the result was "destination Port Unreachable"
try a traceroute.

---

### Post by Jerriy on 2016-08-25
OK things have gone from bad to worse - I can't even get the GUI started  now  Looks like I should do  what I should have done earlier anywayv  (reinstall the whole ubutnu  - what I need now is a reset, not tinkering at the margins.  This is not a hobby PC - I don't have time to spend days on here right now   I'll just reinstall ubuntu but this time with a different partition (make room for another distro like Mint cuz I only have ubuntu now and that turned out to be a bad idea w/ no failsafe since ubuntu has no inbuilt troubleshoot system that simply resets system files to their default state.

---

### Post by TheFu on 2016-08-26
> **Jerriy said:**
> OK things have gone from bad to worse - I can't even get the GUI started  now  Looks like I should do  what I should have done earlier anywayv  (reinstall the whole ubutnu  - what I need now is a reset, not tinkering at the margins.  This is not a hobby PC - I don't have time to spend days on here right now   I'll just reinstall ubuntu but this time with a different partition (make room for another distro like Mint cuz I only have ubuntu now and that turned out to be a bad idea w/ no failsafe since ubuntu has no inbuilt troubleshoot system that simply resets system files to their default state.

If it used to work, put things back the way they were. Backups are handy for that.  Linux doesn't force anyone to do backups, but it is still a very good idea. The flexibility is there to use or not. That is the common *failsafe* deployed, versioned backups.  Mint won't be much different, but feel free to try it out.

Another option is to use a liveCD. That will use default configs. If everything works with a live-boot, then we know it isn't the hardware or something external to the system causing the issues.

Sorry you don't feel like we've been helpful.

---

### Post by Jerriy on 2016-08-26
Yea I didn't do backup - I skipped it since I wasn't prompted at the installation. Now I know that's a must. I do have the live CD.

---

### Post by TheFu on 2016-08-26
> **Jerriy said:**
> Yea I didn't do backup - I skipped it since I wasn't prompted at the installation. Now I know that's a must. I do have the live CD.

If you expect to be prompted for everything that should be done on a computer, I suspect use will be a very limited.  No computer "just works" correctly out of the box. NONE.

Just in case nobody told you this ... Every computing device needs backups unless the entire OS is downloaded off the internet every time it is powered up - like a Chromecast or Roku is.  All smartphones need to be backed up. All laptops, chromebooks, Linux (any flavor), Windows, OSX computers all need to be backed up.  Your home router needs to be backed up too, unless it is running stock settings (which probably is a bad idea).

Linux is about flexibility. It is flexible to do what you want, but like all Unix-based systems, it is YOUR responsibility to run the computer, not the other way around.  > With great power comes great responsibility.

---


---
title: "Possible to have Thunderbird as Firefox's mail client?"
date: 2009-11-30
forum: New to Ubuntu
---

### Post by al.adab on 2009-11-30
Is it possible to link Thunderbird 2.0.0.23 to Firefox 3.5.5 as the latter's mail client (like in the Seamonkey suite, for instance)? 

What I'm after is the possibility of 

a) Firefox showing an alert when a message arrives in my inbox (in Thunderbird)
b) launching Thunderbird and/or opening the message from Firefox

I know that launching both Firefox and Thunderbird on start-up is just as simple...just a thought. If it were possible it'd be great, though...

---

### Post by ukripper on 2009-11-30
a) there is already notification for thunderbird on on all OSs. So why firefox notification is needed?

b) if you running thunderbird why you want firefox to display message there? Why use thunderbird in first place then, just run default mail client from your provider in  firefox?

---

### Post by al.adab on 2009-11-30
you're perfectly right about the alert, I was just wondering if launching Thunderbird from Firefox is possible - like it is on Windows (where if I'm not mistaken you can place a mail icon somewhere in Firefox?). No big deal :)

---

### Post by ukripper on 2009-11-30
> **al.adab said:**
> you're perfectly right about the alert, I was just wondering if launching Thunderbird from Firefox is possible - like it is on Windows (where if I'm not mistaken you can place a mail icon somewhere in Firefox?). No big deal :)

What extension you use on windows firefox for that?

---

### Post by al.adab on 2009-11-30
have no idea, haven't been on windows for quite a while, I just seem to recall noticing it one day on a colleague's pc - somehow he used thunderbird through firefox (without launching both, just firefox), but I might be mistaken...

---

### Post by ukripper on 2009-11-30
Never heard of that kinda extension, as it defies the whole purpose of thunderbird in first place. Why not just use firefox and provider's mail client then?

---

### Post by al.adab on 2009-11-30
I agree it does - I've been using the Gmail offline option for a couple of years, and am now looking into alternatives as Google Gears is giving me a hard time - for some reason an error message keep popping up despite of re-installing it, etc. I posted a thread on it but it looks like it's probably Google that needs to fix it. 

Gmail offline is ok, except that it's got some limitations. I don't like Evolution at all, for some reason, I tried it and just can't use it. But no worries, Thunderbird works great, and all I need to do is to remember to launch both at start-up. No need for an extension :) as I said it was just a thought. Thanks for taking the time to look into this.

---

### Post by ukripper on 2009-11-30
No problem mate. i think it is still possible via extensions but you will still need thunderbird running.

---

### Post by running_rabbit07 on 2009-11-30
OP, I think I see what you want and here is how I think you go about it. Go to System>Preferences>Preferred Applications and select Mozilla Thunderbird.

---

### Post by running_rabbit07 on 2009-11-30
If you search through Synaptic Package Manager, there are a few different email alert apps that work with Thunderbird, but I don't know if they will do what you want.

---

### Post by al.adab on 2009-11-30
Tried out the Thunderbird application through Synaptics but don't really understand how to activate it. Also linked Thunderbird to Firefox as you suggest, but don't see any difference. This is ok, though, as I'm getting used to launch Thunderbird at start-up :) Thanks everyone for their feedback.

---

### Post by EssexEagle on 2009-11-30
Check out [Thunderbird Biff]("https://addons.mozilla.org/en-US/firefox/addon/3788").

HTH :-)

---

### Post by al.adab on 2009-11-30
Thank you EssexEagle!!!

It looks like the solution. Except that...well, I don't understand the Java Script Application error message I get when I click on the Biff icon on my Firefox toolbar: 

*Until you specify a path to your email client via the options panel, this function is disabled*.

I installed Biff both in Firefox and Thunderbird. In Firefox, if I go to Tools>Add-ons>Thunderbird Biff (preferences), it looks like I need to fill out the "path to your Thunderbird executable file". 

Do you think this path is what the Java error message is about? How can I find such path?

---

### Post by teward on 2009-11-30
It's asking you to manually state where on your computer thunderbird launches from.  Where its stored, I'm not sure, at least on your computer I'm not.

---

### Post by al.adab on 2009-11-30
I see. Could the path then be some of the pattern 

*file:///home/user/Thunderbird* ? 

How do I actually find out what the exact path is - where Thunderbird is?

---

### Post by EssexEagle on 2009-11-30
> **al.adab said:**
> Thank you EssexEagle!!!

It looks like the solution. Except that...well, I don't understand the Java Script Application error message I get when I click on the Biff icon on my Firefox toolbar: 

*Until you specify a path to your email client via the options panel, this function is disabled*.

I installed Biff both in Firefox and Thunderbird. In Firefox, if I go to Tools>Add-ons>Thunderbird Biff (preferences), it looks like I need to fill out the "path to your Thunderbird executable file". 

Do you think this path is what the Java error message is about? How can I find such path?

Try
```
/usr/bin/thunderbird
```
(that's the file that executes when you ask Ubuntu to run Thunderbird).



p.s. Most (all?) programs in Ubuntu are found at /usr/bin/<name>.  To check what file is executed when you run a particular program/command, you can use the "which" command in the terminal.  e.g.
```
which thunderbird
```
will return
```
/usr/bin/thunderbird
```

---

### Post by al.adab on 2009-11-30
Thank you!!!

Just found out that to get it you need to do the following in Terminal: 

[I]
~$ type thunderbird[/I]

and hit enter. In my case (as EssexEagle guessed: thanks!) the path is

I]/usr/bin/thunderbird[/I]

Great stuff. And it works :)

---


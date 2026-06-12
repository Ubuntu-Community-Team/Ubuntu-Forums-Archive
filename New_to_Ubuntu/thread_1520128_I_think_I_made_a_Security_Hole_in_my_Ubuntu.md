---
title: "I think I made a Security Hole in my Ubuntu"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by Andavane on 2010-06-29
I was ordering some medicine from my local surgery:

[http://www.staploe.com/index.php/prescriptions/order-on-line]("http://www.staploe.com/index.php/prescriptions/order-on-line")

when I went to check the order I had a warning flash up about unsafe content.
I made an exception and got taken here:

[http://www.daisyhilldesigns.co.uk/shop/]("http://www.daisyhilldesigns.co.uk/shop/")

for some reason. Having "made exception" (thinking it was my surgery) I want to retract it. I've tried looking in security in firefox, but can't see that site there.

So I want to get that 2nd site off.

Regards

John

---

### Post by robsoles on 2010-06-29
> **Andavane said:**
> I was ordering some medicine from my local surgery:

[http://www.staploe.com/index.php/prescriptions/order-on-line](http://www.staploe.com/index.php/prescriptions/order-on-line)

when I went to check the order I had a warning flash up about unsafe content.
I made an exception and got taken here:

[http://www.daisyhilldesigns.co.uk/shop/](http://www.daisyhilldesigns.co.uk/shop/)

for some reason. Having "made exception" (thinking it was my surgery) I want to retract it. I've tried looking in security in firefox, but can't see that site there.

So I want to get that 2nd site off.

Regards

John

In Firefox (provided you are in similar version to mine) open

'Edit'->'Preferences'

Choose 'Advanced' in very top of dialog/page that opens

Choose 'Encryption' tab, click 'View Certificates'

In new dialog/window that opens choose 'Servers' tab

Find the offending site you don't want as an encryption security exception and select it.

Click 'Delete'

Close extra windows, that should do what you appear to be asking for.

???

---

### Post by iponeverything on 2010-06-29
most warnings like that are related to what is called "drive-by" attacks that only affect windows. That said, if you restart your system any run-away process that may have started, will be gone. Also, clearing you cookies and cache and should also clear out any exceptions that firefox was using.

---

### Post by robsoles on 2010-06-29
Sorry, just re-considered what exception you say you added and I think you mean that you clicked something on a page you basically trust and the browser showed you a page with a thick kind of border and text in the middle said that you were headed for unsafe content with a link or button nearby to add an exception.

The website won't be listed in the location I pointed out before and I am not sure where or if this website is stored as an exception or whether the browser simply let you follow the link that time and will merrily warn you again if you try to open that page again.

I am rather hoping (for your sake) that you entered no credit card or banking details into any browser before restarting your computer after allowing your browser to hit that page and particularly into any page loaded under that exception!

I googled a little when I realised my mistake about your query and I can't find anything conclusive that your browser recorded something - just always make sure you can read the address bar before entering anything that you want to be secure between you and any website!

If you are particularly stressed it is actually easy to totally scrub all existing settings and exceptions for firefox without even un-installing it. Are you stressed enough to want to scrub it like that?

---

### Post by Andavane on 2010-06-30
> **robsoles said:**
> In Firefox (provided you are in similar version to mine) open
'Edit'->'Preferences'
Choose 'Advanced' in very top of dialog/page that opens
Choose 'Encryption' tab, click 'View Certificates'
In new dialog/window that opens choose 'Servers' tab
Find the offending site you don't want as an encryption security exception and select it.
Click 'Delete'
Close extra windows, that should do what you appear to be asking for.
???

Thanks very much. That did the trick!
Another lesson to notch up!
:p

---

### Post by robsoles on 2010-06-30
> **Andavane said:**
> Thanks very much. That did the trick!
Another lesson to notch up!
:p

Please figure out how to mark this thread 'solved' and do so, glad I could help.

---

### Post by Andavane on 2010-06-30
> **robsoles said:**
> Sorry, just re-considered what exception you say you added and I think you mean that you clicked something on a page you basically trust and the browser showed you a page with a thick kind of border and text in the middle said that you were headed for unsafe content with a link or button nearby to add an exception.

The website won't be listed in the location I pointed out before and I am not sure where or if this website is stored as an exception or whether the browser simply let you follow the link that time and will merrily warn you again if you try to open that page again.

I am rather hoping (for your sake) that you entered no credit card or banking details into any browser before restarting your computer after allowing your browser to hit that page and particularly into any page loaded under that exception!

I googled a little when I realised my mistake about your query and I can't find anything conclusive that your browser recorded something - just always make sure you can read the address bar before entering anything that you want to be secure between you and any website!

If you are particularly stressed it is actually easy to totally scrub all existing settings and exceptions for firefox without even un-installing it. Are you stressed enough to want to scrub it like that?

Hi again,
I was going through your first point and missed this one;
You are correct in what you write earlier - I totally trust the first site; after I'd made the order my helper asked me to click "back" on the browser as he wasn't sure one order went onto the list. It was our attempt to see what we'd ordered (it's our local dispensary, you send the order and go to collect the items  2 days later -- they don't send confirmation, & they only take money when you go to get the goods). It was during this process that I was 'dragged' into a site where they *do* take money, but I clicked that I trusted them, thinking they were the first site.

So cheers, I am not stressed, but I'd be glad to know how to wipe everything, in case a similar situation presents itself, if you'd like to tell me

:popcorn:

NB: Marking thread as SOLVED had been effected this end :)

(It's in thread tools at the top: I mention this as at one point they removed that option, and you had to do it manually.)

---

### Post by robsoles on 2010-06-30
Thanks for info about marking thread solved, I am yet to make a thread because I keep fluking my problems just as I am about to post a thread asking for a solution.


A quick and clean enough way to scrub every last setting, bookmark and cookie and 'other' you have in firefox is to open your 'home' folder (top of tree in 'places') and then press [CTRL]+[H] to show hidden files, double click '.mozilla' and then select "firefox" - press [Delete] on it's own to stick it in your garbage bin (where you can restore it from if needed/desired) or '[Shift]+[Delete]' to make it go away permanently. Or you can rename it to something like 'perhaps-restore-firefox-settings' if very worried about recovering when it turns out the browser knew a password you can't otherwise recover or remember!

That 'other' website is probably a trusted colleague/sister site of the one you trust which simply doesn't have a certified SSL certificate (based on fact that my initial response was the answer) - all this means is that they didn't pay thousands of dollars to a certificate authority to certify that their encryption certificate is genuine and belongs to them.

The second scenario my second post tries to 'sort of cover' is where a site is either criminal itself or has been compromised by criminals leaning toward the idea that iponeverything had taken from your original post.

It is both relevant and a pity that sites that want to have a 'https' address (meaning you should be communicating with them at least fairly securely) need to pay through the nose to another company so your browser won't say they may be false and misleading.

HTH - just ask about similar stuff until you are sure enough of what you are doing out there!

---


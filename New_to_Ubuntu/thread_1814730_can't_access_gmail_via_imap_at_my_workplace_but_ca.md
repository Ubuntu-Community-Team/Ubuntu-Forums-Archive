---
title: "can't access gmail via imap at my workplace but can elsewhere"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by hanzj on 2011-07-30
I can't access my gmail via Imap when at work. 
I can access the webmail gmail at work.
I can access my gmail via imap at other places (home, on the road)

Without asking the network admin, how can I find out whether my workplace IT is blocking certain ports, or somehow blocking imap?

And how can I bypass the blocking?

Clients used: thunderbird 5, windows live mail, outlook express, postbox

---

### Post by alphacrucis2 on 2011-07-30
> **hanzj said:**
> I can't access my gmail via Imap when at work. 
I can access the webmail gmail at work.
I can access my gmail via imap at other places (home, on the road)

How can I find out whether my workplace IT is blocking certain ports, or somehow blocking imap?

And how can I bypass the blocking?

You ask your network admin.

---

### Post by hanzj on 2011-07-30
I'd like to get answers without asking the network admin. how can i do so?

---

### Post by aysiu on 2011-07-30
When you're accessing it via IMAP, what client are you using?

I know that [with Fortigate, the Gmail server certificate gets decrypted and then Fortigate creates its own Gmail certificate for the client](http://www.google.com/search?hl=en&source=hp&biw=1108&bih=699&q=fortigate+certificate+gmail&oq=fortigate+certificate+gmail&aq=f&aqi=&aql=&gs_sm=e&gs_upl=480l4991l0l5286l29l23l1l3l1l1l247l3171l0.16.3l19l0), which is a mismatch (God knows why they do it this way), and then Outlook will just reject the certificate. If you use Thunderbird, you'll be prompted about the certificate mismatch and then asked if that's okay anyway.

---

### Post by hanzj on 2011-07-30
aysiu,
i've used postbox, thunderbird 5, windows live mail, outlook express.

in thunderbird, the error message does not mention certificate mismatch.

The sort of error message I get are:
-- regarding password and username (and, yes, i've made sure i did [email]username@gmail.com[/email] and made sure i correctly entered password

---

### Post by aysiu on 2011-07-30
Well, if it's not the certificate mismatch issue, it's definitely *something* with your network, so you have to ask your network administrator, even though I know you don't want to.

---


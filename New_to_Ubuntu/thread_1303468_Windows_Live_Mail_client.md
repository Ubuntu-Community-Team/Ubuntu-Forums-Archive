---
title: "Windows Live Mail client?"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by jonathanstratford on 2009-10-28
Hi,

I'm strongly considering moving to Ubuntu from Windows XP. I hope this is the correct forum for my particular query.

I'm pretty sure almost everything I want to use is available, but one of the things I think is not is an email client that works in the same way as the Windows Live Mail client does (not the web page) to check Hotmail on Windows -- I don't want to use POP to access the email, and I'm not sure what the Windows client uses, since IMAP isn't available for Hotmail, but I want to be able to access hotmail such that I can read all my emails (both old and new) both in the webpage or in the email client, and changes I make in either (marking as read/unread, moving, deleting) are reflected in both automatically. As i understand it, if I use a POP client, the emails will be downloaded to my machine (optionally deleted from the server), and changes I make won't be reflected, which isn't suitable for my needs. I hope this is clear, I'm aware it might not be.

I recently tried using Mozilla Thunderbird on Windows (when switching from Outlook Express, which also handled Hotmail the way I want), but this does not allow access in the way I require, so I'm assuming the same will be true of this product on Linux.

I've looked up Windows Live Mail in the Wine Application Database ([http://appdb.winehq.org/objectManager.php?sClass=application&iId=7436](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7436)) which seems to indicate that it won't run, but it seems this is an old version of Wine, so I'm not sure if it's indicative. I guess I can put the Live CD in and try installing it and see what happens, but I am hoping that others may be able to advise -- I'd rather not start going round in circles with something that's overly complicated if others have found a far better method.

Does anyone have any experience with this, and have any suggestions? I tend to run my email client all the time, so firing up a Windows VM (which I intend to use for one or two things) just to check my email in a convenient way is something I'd rather not do. I'm open to using other email clients (I don't know the names of many on Linux), but I suspect that Windows Live Mail does something proprietary that other clients cannot do.

Thanks a lot for your help. This is basically the only reason I have for not switching at the moment. If any suggestions require using a terminal, I'm not afraid of that as I've used Linux a fair amount in the past at work, but I would prefer if the email client is graphical :)

Jonathan

---

### Post by snkiz on 2009-10-28
What you are describing is IMAP. And since you say hotmail doesn't support IMAP (I don't know, I don't use it.) I would conclude that windows live is using IMAP and just not sharing. The best workaround I can think of would be to filter your hotmail account through gmail witch does have IMAP available to the public.

On a side note, why would you go to the trouble of getting rid of xp only to continue to use their crappy infrastructure?

---

### Post by howefield on 2009-10-28
> **snkiz said:**
> The best workaround I can think of would be to filter your hotmail account through gmail witch does have IMAP available to the public.

Or simply move to gmail completely for email provision.

One minor point that I like about gmail is that it doesn't append adverts to the bottom of very email you send in the way that most free providers do.

---

### Post by snkiz on 2009-10-28
True, but gmail's abilty to to use pop access to get into another email  is a handy transition tool.

---

### Post by jonathanstratford on 2009-10-28
Thanks for all your replies.

snkiz said:
On a side note, why would you go to the trouble of getting rid of xp only to continue to use their crappy infrastructure? 	

I'm not sure if you mean XP (in a VM as I mentioned) or Hotmail...I'm guessing the latter -- I use hotmail as I have for many years, so it would be quite a large amount of effort to change everywhere that knows the address, which I was hoping a change of OS wouldn't require! Having said that, maybe it says more about Microsoft than anything else. I know some people don't like hotmail, but it works for me, which is all that really matters to me!

I do already have a gmail account, but I don't use it too often; I will try to see if it will let me do what I want -- it sounds like it won't, as it only does POP access.

howefield said:
One minor point that I like about gmail is that it doesn't append adverts to the bottom of very email you send in the way that most free providers do.

Oddly, using Windows Live Mail program (as opposed to the webpage) does NOT seem to add adverts to the email either.

Being entirely new here, I don't know if what you guys have said means there is no solution (just gmail/other mail-related workarounds), but if anyone has any thoughts on achieving my request without needing to change email account, that would be great!

Thanks again for your time.

Jonathan

---

### Post by Dougie187 on 2009-10-28
It would seem, since the mail fetcher in gmail can pull from hotmail, that you should be able to set up evolution or thunderbird to pull email from hotmail as well, you just have to use pop3 to check it.

However, I would seriously recommend as previously mentioned getting a gmail account and having that pull the hotmail email through it. That way you get to keep both emails, but you can also just check your gmail with imap. Also, gmail's spam filter is FAR superior to hotmails.

But this is just my recommendation, and you can choose to do it or not.

If you are looking to pull mail from hotmail using pop3, you should be able to use the server (i think) pop3.live.com, but there are a couple other choices.

---

### Post by snkiz on 2009-10-28
just comming to make those points. You don't need to get all new mail, hand the address to all your friends. just forward everything from hotmail to gmail then use IMAP through your mail client of choice.

---

### Post by SunnyRabbiera on 2009-10-28
Evolution might be helpful here too, but really it depends on your settings on your hotmail account.
But in the end you may have to use pop3 to access it, I know you dont like the idea but yeh I dont think hotmail uses IMAP...

---

### Post by dj-toonz on 2009-10-28
you can get IMAP in Hotmail under Linux but you have to pay for the feature to be able do that (to be able uses calendars & the likes), you can get email via POP3 tho for free not IMAP, IMAP support for free is only via Windows Live mail & Live mail Desktop under Windows

Pop3 server settings for hotmail

POP3.live.com
SMTP.live.com
use SSL for both incoming & outgoing Security settings
Use your full email address for user name to login

---

### Post by noelvh on 2009-10-28
Gmail, gmail, gmail!!!!!!! God I love Gmail. I have 3 gmail accounts plus my own Google apps domain, with my own domain "theorky.net". I get 200 email address for $10.00 a year with google apps.

Did I say I love Gmail?

Noel

---

### Post by Dougie187 on 2009-10-28
Just so you know. Hotmail doesn't support forwarding. At least last time I checked it didn't.

---

### Post by HybridZero on 2009-10-28
One more quick note, Gmail DOES in fact support IMAP. I understand the hassle of moving everything from Hotmail over to Gmail and updating contact information and whatnot, but realistically, Gmail is far more friendly to desktop clients that Hotmail is - it's worth the effort to get the added accessibility.

---

### Post by jonathanstratford on 2009-10-29
I've done a bit of investigating, and unfortunately it seems, being Microsoft, WLM Desktop isn't using IMAP at all, but "DeltaSync". Why use a nice existing protocol when a new proprietary one will do..?

I don't know if I've just not used it enough, but I've never particularly got on with the GMail web interface...I'll try it again at some point. I've not noticed an IMAP option for clients, either, but I'll look harder :)

Thanks for all your help guys.

---

### Post by snkiz on 2009-10-29
Hotmail does support pop3 though. Gmail can fetch pop3 accounts.
If you have trouble liking the web interface I'd suggest you have a look at the Google labs addons. They many even give you a new idea you really like.

---


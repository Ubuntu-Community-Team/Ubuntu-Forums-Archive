---
title: "Thunderbird rejecting request to collect Hotmail"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by Roger Allott on 2009-10-01
I'm getting an odd error message when launching Thunderbird, which has been solely used to store my Hotmail emails.

Hotmail now seems to be rejecting my password, as the error message is:
```
Sending the password did not succeed. 
Mail server localhost responded: negative vibes from xxxxxx@hotmail.com
```

Something also that's odd is that Thunderbird is now asking me for my Hotmail password, whereas in the past it knew it and never prompted me for it.

Does this problem look familiar to anyone? If so, could you please explain how I can resolve it?

---

### Post by stalkier on 2009-10-01
> **Roger Allott said:**
> I'm getting an odd error message when launching Thunderbird, which has been solely used to store my Hotmail emails.

Hotmail now seems to be rejecting my password, as the error message is:
```
Sending the password did not succeed. 
Mail server localhost responded: negative vibes from xxxxxx@hotmail.com
```

Something also that's odd is that Thunderbird is now asking me for my Hotmail password, whereas in the past it knew it and never prompted me for it.

Does this problem look familiar to anyone? If so, could you please explain how I can resolve it?

I once had a similar issue with Gmail. I had to log into the Gmail website and change my password. Once I did that is was ok. You might try doing that and post back if it worked or not.

---

### Post by halitech on 2009-10-01
how do you have Tbird set up to collect email? Reason I'm asking is this
```
Mail server localhost
```
indicates it is looking to your local computer (localhost) for the mail.

---

### Post by grizzler on 2009-10-01
> **Roger Allott said:**
> Hotmail now seems to be rejecting my password, as the error message is:
```
Sending the password did not succeed. 
Mail server localhost responded: negative vibes from xxxxxx@hotmail.com
```
That error indicates you're still using the WebMail add-on for Hotmail. You do know it's no longer required, don't you? You can make Thunderbird collect mail from Hotmail by using these settings:

Servername: pop3.live.com
Port: 995
Security settings: SSL

See [http://windowslivewire.spaces.live.com/blog/cns!2F7EB29B42641D59!32413.entry](http://windowslivewire.spaces.live.com/blog/cns!2F7EB29B42641D59!32413.entry) for more information.

---

### Post by Roger Allott on 2009-10-01
> **grizzler said:**
> That error indicates you're still using the WebMail add-on for Hotmail. You do know it's no longer required, don't you? You can make Thunderbird collect mail from Hotmail by using these settings:

Servername: pop3.live.com
Port: 995
Security settings: SSL

See [http://windowslivewire.spaces.live.com/blog/cns!2F7EB29B42641D59!32413.entry](http://windowslivewire.spaces.live.com/blog/cns!2F7EB29B42641D59!32413.entry) for more information.

Ah! Thanks for that. I have the Webmail and the Webmail - Hotmail add-ons.

Bizarrely though, when I went to check which versions of the extensions I was using, I noticed that updates were available for them. So, I thought, I'll update them and see what happens, and of course that bleedin' well went and fixed it!

I don't know now whether I should leave the settings as is, or uninstall the extensions and set up my account as you describe. Any ideas?

---

### Post by grizzler on 2009-10-02
> **Roger Allott said:**
> I don't know now whether I should leave the settings as is, or uninstall the extensions and set up my account as you describe. Any ideas?

Well, as long as it works you might as well leave it alone.

Next time MS makes changes to the site, the add-on will probably fail again. That may be as good a time as any to switch.

Personally, I would switch now (if I hadn't done so months ago...). But that's just me.

---

### Post by Roger Allott on 2009-10-02
> **grizzler said:**
> Well, as long as it works you might as well leave it alone.

Next time MS makes changes to the site, the add-on will probably fail again. That may be as good a time as any to switch.

Personally, I would switch now (if I hadn't done so months ago...). But that's just me.

OK, so I think it might indeed be best to switch now, but should I uninstall the two Webmail extensions and then change my settings, or should I simply leave them (perhaps disabled??) and simply make changes to my account details in Thunderbird?

---

### Post by grizzler on 2009-10-02
Why would you want to keep the add-ons?

As soon as you've changed your account settings, the add-ons are no longer of any use. The WebMail add-on itself might be I suppose, if you have other webmail accounts besides Hotmail, but the Hotmail add-on wouldn't serve any purpose anymore.

If you feel uncertain about changing things, you could leave them installed until you're sure the direct method works properly.

---

### Post by debiant on 2009-10-12
> **grizzler said:**
> That error indicates you're still using the WebMail add-on for Hotmail. You do know it's no longer required, don't you? You can make Thunderbird collect mail from Hotmail by using these settings:

Servername: pop3.live.com
Port: 995
Security settings: SSL

See [http://windowslivewire.spaces.live.com/blog/cns!2F7EB29B42641D59!32413.entry](http://windowslivewire.spaces.live.com/blog/cns!2F7EB29B42641D59!32413.entry) for more information.

Thank you Grizzler!

:P

---

### Post by sandyd on 2009-10-12
p.s. you might use port 587 for your SMTP address instead of 25 cause many ISPs block port 25.

---

### Post by dirtyhabanero on 2010-07-28
hey guys, used this new method of connecting straight to pop3.live.com and it worked. had a bit of trouble with the outgoing setup but put my settings to STARTTLS, no authentication, smtp.live.com and on port 25. 

I found it really strange though because I went to the trouble of installing the webmail add-on and getting things working great...and then it just stopped working after about 2 days. :confused:strange. 

anyways, thanks!

---


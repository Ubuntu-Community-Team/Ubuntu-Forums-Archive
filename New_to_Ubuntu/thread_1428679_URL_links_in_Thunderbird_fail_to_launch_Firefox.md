---
title: "URL links in Thunderbird fail to launch Firefox"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by boxcorner on 2010-03-13
**Background:**
Using two Mozilla applications in Ubuntu 9.10 Karmic Koala.
**Problem:**
Clicking, or double-clicking, on URL links in e-mails received using Thunderbird Shredder v3.0.3pre fails to launch Firefox Namoroka v3.6.2pre
**Tried:**
System > Preferences > Preferred Applications
Web Browser > Firefox > Open link in new wndow
Mail Reader > Thunderbird 3.0
Accessories > Terminal 
whereis firefox
firefox: /usr/bin/firefox /etc/firefox /usr/lib/firefox /usr/share/firefox
which firefox
/usr/bin/firefox
Applications > Accessories > gedit Text Editor
Created a file called user.js (none existed before) containing:
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.ftp", "/usr/bin/firefox");
saved it in my Thunderbird profile folder
home > me > .thunderbird-3.0 > xxxxxxxx.default
**Checked:**
Thunderbird > Edit > Preferences > General > Config Editor > about:config
network.protocol-handler.app.ftp;/usr/bin/firefox
network.protocol-handler.app.http;/usr/bin/firefox
network.protocol-handler.app.https;/usr/bin/firefox 
**Result:**
No change.
Links still don't work. 
**Request:**
What am I doing wrong?  Please!

---

### Post by ankspo71 on 2010-03-13
Hi,
I'm not sure if this will help, but in order for me to get thunderbird 3.* to open http links I had to tell it to do it when it said something like: "Thunderbird does not know how to open this type of file." Right there I told it to open with firefox by browsing to /usr/bin/firefox. Now when I go into thunderbird preferences under the attachments tab, it shows firefox as the handler of http attachments (which are not supposed to be attachments because they are urls). See screenshot:
I'm using Ubuntu Lucid (test release) with thunderbird 3.0.1
hope this helps

---

### Post by boxcorner on 2010-03-13
@ ankspo71
Many thanks! So, this is what I did:
Edit > Shredder Preferences > Attachments > Content Type: http
select Use other from Action drop-down then browse to /usr/bin/firefox
select Use firefox from Action drop-down
that seems to work for explicit links in e-mails (ie ones that show the URL)
however, when clicked, some links invoke a Launch Application window instead
for inexplicit links (ie ones that don't show the URL) but lead to https instead
Choose an Application > Choose > browse to /usr/bin/firefox
then click on Choose again and select Firefox
tick/check Remember my choice for https links
hope this helps someone else

---

### Post by kstarkey1 on 2010-03-21
> **boxcorner said:**
> @ ankspo71
Many thanks! So, this is what I did:
Edit > Shredder Preferences > Attachments > Content Type: http
select Use other from Action drop-down then browse to /usr/bin/firefox
select Use firefox from Action drop-down
that seems to work for explicit links in e-mails (ie ones that show the URL)
however, when clicked, some links invoke a Launch Application window instead
for inexplicit links (ie ones that don't show the URL) but lead to https instead
Choose an Application > Choose > browse to /usr/bin/firefox
then click on Choose again and select Firefox
tick/check Remember my choice for https links
hope this helps someone else

Thanks much!  I was going thru this same thing on my wife's laptop, and I thought I'd run out of options.  This fix did the trick!  Awesome!

---

### Post by snake_eyes on 2010-03-25
I have the same issue, I'm not able to open directely the wmv files, I check the > attachments and I didn't found the wmv in the list, so how to add new extensions?

Please note that currently when I double click on the file inside the email it ask me to where I wanna save it, I wont this, what I need is the open it instead of saving it

Cheers,

---

### Post by robertj20112 on 2010-04-03
Thanks.  Solved it for me, too!

---

### Post by snake_eyes on 2010-04-03
> **robertj20112 said:**
> Thanks.  Solved it for me, too!

How?

---

### Post by boxcorner on 2010-04-04
> **snake_eyes said:**
> ... I didn't found the wmv in the list
...
Not sure, but my guess is you'd have to use an emulator such as Wine, because WMV is proprietary.  WMV (ie Windows Media Video) is a compressed video compression format for several proprietary codecs developed by Microsoft.

---

### Post by ankspo71 on 2010-05-01
> **snake_eyes said:**
> I have the same issue, I'm not able to open directely the wmv files, I check the > attachments and I didn't found the wmv in the list, so how to add new extensions?

Please note that currently when I double click on the file inside the email it ask me to where I wanna save it, I wont this, what I need is the open it instead of saving it

Cheers,

I imagine is would be the same as the above advice, but to tell it to open with a video player capable of playing wmv files. I think VLC is capable, so if you have that player installed, the path to VLC would be /usr/bin/vlc.

---

### Post by betlog on 2010-07-22
The above jigggery-pokery solved it for me too... weird.. particualrly because it used to work fine before


just as possibly useful data to debuggers - here is a synopsis/comments of the problem:

single/double clicking on a hyperlink in thunderbird 3.0.5 does nothing
right click and 'open link in browser' does nothng
however:
click and drag the link from thunderbird to a firefox tab/window works  fine

some observstions of things I have done that may be related:

I have tried adding:
 network.protocol-handler.app.http = /usr/bin/firefox
with no effect

I know thnderbird hyperlinks worked before. 
There may have been a correlation between when i decided to stop using  knetworkmanager and start using wicd, and when the URIs stopped working  in thunderbird.
At this time I also applied
 toolkit.networkmanager.disable = true
which does not seem to have any effect when i set it to default(false)  now.

---


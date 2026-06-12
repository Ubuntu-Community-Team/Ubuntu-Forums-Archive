---
title: "Email Hyperlinks to Default Browser not working"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by expatCM on 2010-05-17
Ubuntu 10.04   Thunderbird 3.0.4
Fresh install of Ubuntu.  Copied over the user profile / email.

Hyperlinks do not work.  What I have done to try and fix this is :

1.  In Edit / Preferences / Config Editor change the network.protocol-handler.warn-external entries to true.  There is however no prompt when a link is subsequently clicked.  This article shows that setting.
[http://kb.mozillazine.org/Setting_Your_Default_Browser](http://kb.mozillazine.org/Setting_Your_Default_Browser)

2.  Search the config editor file for any reference of firefox.  Nothing there.

3.  Look at the prefs.js file for any reference of firefox.  Nothing there.

What should I do next?

---

### Post by Peter09 on 2010-05-18
Just to do a sanity check, is firefox set as your defaukt browser? Check in its preferences that it is.

---

### Post by expatCM on 2010-05-18
A sanity check is always good. If I look at System / Preferences / Preferred Applications then Firefox is selected as the browser.

I am not aware of a setting in Thunderbird to select Firefox as a browser other than what should be defined by the network.protocol-handler.

Working the other way round, mailto in Firefox defines Thunderbird and that works.

---

### Post by Peter09 on 2010-05-18
AhAh
 
[http://getsatisfaction.com/mozilla_messaging/topics/html_link_not_working_in_thunderbird_email_body](http://getsatisfaction.com/mozilla_messaging/topics/html_link_not_working_in_thunderbird_email_body)
 
looks interesting
 
and more upto date
 
[http://www.google.com/support/forum/p/Chrome/thread?tid=479e566824181986&hl=en](http://www.google.com/support/forum/p/Chrome/thread?tid=479e566824181986&hl=en)

---

### Post by expatCM on 2010-05-18
Well I looked at the title and thought this has to be it. But then I read into the details and nope ...

There is nothing malformed about the links in the messages I get.  I can copy and paste into the browser and they work.  But the other point there is that even if they were malformed I "guess" that they would open the browser but then not the page ... 

I did notice one interesting item in the google link though and I will be investigating that in a minute ...

---

### Post by expatCM on 2010-05-18
I guess what is bothering me is that this is a fresh install as of yesterday.  So how can this have gone wrong..  The only none fresh bit was to copy over the old profile since this has all the messages ....  Can something have got corrupted in the profile perhaps .....

---

### Post by Peter09 on 2010-05-18
Note that I posted a second link - this is an April 2010 problem.

---

### Post by expatCM on 2010-05-18
Yes, I had not noted the date significance ...  perhaps there will be a patch :)

I will be working through some of these suggested approaches a bit later ..  I think they also need understanding rather than simply copying ...

---

### Post by expatCM on 2010-05-24
I have been working on this but not making any progress.

I have edited the profile prefs.js file to add the following

user_pref("network.protocol-handler.app.ftp", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");

This shows up in the Thunderbird edit Preferences / Advanced / Config Editor so I know that the program sees the setting.

I have also tried to state this without the /usr/bin/ path but no change.

But still, if I double click on a link or right click on a link and select Open in Browser ...  nothing happens.

Any suggestions welcome ........

---

### Post by expatCM on 2010-05-24
I have just found the solution ......   well it works for me.  A LOT of people seem to have this problem and so I post what I found here.

Scroll down this link to the posting from Kevin
[http://getsatisfaction.com/mozilla_messaging/topics/link_in_thunderbird_email_wont_open_in_browser](http://getsatisfaction.com/mozilla_messaging/topics/link_in_thunderbird_email_wont_open_in_browser)

I repost what he said here
> 
- Open TB
- Click 'Edit'
- Click 'Preferences'
- Click 'Attachments' tab
- You will see 'Content Type' listed (mine shows 'http' and 'https')
- Under 'Action' select 'Use Other'
- Locate firefox directory (~/usr/lib/Firefox3.6.x) and open it
- Double click the 'firefox' icon. (it will be called 'firefox' without anything else in the file name)
- Repeat for both 'Content Types'
- 'Action' should now read 'Use firefox'
- Close. You're all set. 

---


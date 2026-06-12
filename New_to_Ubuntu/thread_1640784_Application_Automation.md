---
title: "Application Automation"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by lenscom on 2010-12-08
I have been using Ubuntu 10.04 desktop since it was released earlier this year and think its fantastic.  I have replaced most of my Desktop and Laptop Microsoft OSEs with Ubuntu.

I now wish to progress to using the Linux Terminal and gedit to produce pre-programmed batch files that will automatically run at certain times of day (i.e. to run Firefox with a predefined url address) to automatically administer the configuration of my home IP Security Cameras (i.e. to switch on/off the flashing LED indicator). I have progressed a little in producing a batch file that will simply do the following:

#!/bin/bash
Firefox <URL> &

The URL also contains the IP Security Camera configuration commands which I already know and can apply.  However, when Firefox opens the web-page I am presented with the normal authentication window requesting id + pw. As yet I do not know how to automatically enter the id + pw via the batch file commands. Once authentication is processed the IP Camera configuration will be automatically updated (e.g. putting Flashing LED either ON or OFF)

Also, I have not yet found out how to run the batch file at pre-defined times of day. I think a cron job might be needed but need help / guidance in linking the program batch file to a cron job.

Apologies for my novice approach above and if my terminology isn't correct but would much appreciate some guidance if someone is happy to accept the challenge with helping me resolve the above.

Best Regards
Lenscom :)

---

### Post by Wobblybob on 2010-12-10
Can't help with the password bit but you may want to look at the command line browser called lynx which can be used in scripts and is able to record keystrokes you used to get into a web site then play them back in a script. This may be an option to auto login but I've not used it yet.
edit; Try
log your actions in lynx with this option

lynx -cmd_log=~/filename [http://thesiteURL.com](http://thesiteURL.com)

once you have recorded your actions in the file named filename you can do that:

lynx -cmd_script=~/filename [http://thesiteURL.com](http://thesiteURL.com)

it should then auto logon [fingers crossed ]


try my blog here for cron.

[[COLOR="Navy"]http://myubuntublog.wordpress.com/2009/08/31/cron-jobs/[/COLOR]]("http://myubuntublog.wordpress.com/2009/08/31/cron-jobs/") 

Good luck..

---

### Post by Cheesehead on 2010-12-10
To run scripts (or anything else at a desired time) use cron. There are loads of cron tutorials just a search engine away.

For sending commands and receiving replies from URLs, you can use wget or curl more easily than firefox. They can both handle logins, get/post, custom URLs, and run headless quite easily. Both also have loads of tutorials just a search engine away.

If you want something easier to maintain, python's urllib module can also easily do it. And cron will launch a python script just as happily as it will launch a bash or dash script.

---

### Post by Girya on 2010-12-11
check this article out for an example of how to script a login and password. 

[http://www.linuxjournal.com/content/use-curl-monitor-your-vonage-phone-bill?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+linuxjournalcom+%28Linux+Journal+-+The+Original+Magazine+of+the+Linux+Community%29&utm_content=Google+Feedfetcher]("http://www.linuxjournal.com/content/use-curl-monitor-your-vonage-phone-bill?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+linuxjournalcom+%28Linux+Journal+-+The+Original+Magazine+of+the+Linux+Community%29&utm_content=Google+Feedfetcher")

basically you look at the page source of the login form to figure out what the variable names are for user and password and pass those to the login script on the web server directly.

---

### Post by lenscom on 2010-12-11
Guys

Many thanks for your guidance. I think I have enough to experiment with for a while and will let you know how successful (or otherwise) I have been.

I find it interesting stuff and (as with most technical stuff) getting started and familiar with it is the hardest bit and then the interesting / fun bit takes over and keeps you going. I'm not over the first hurdle yet but with your help I have a better chance of getting over it.

Once again many thanks
Lenscom :-)

---

### Post by lenscom on 2010-12-14
Hi Guys

I have used lynx as suggested by Wobblybob and it works very well. The Security Camera LED automatically came on with one recorded authenticated script and went off with another.

The next step is to set up cron jobs to get it all automated. Again, not having done it before I need to experiment with configuring cron and will get to you as soon as I have some more results.

Once again thanks to Wobblybob and all for your help
Best Regards
Lenscom :)

---

### Post by lenscom on 2010-12-20
Hi All

I am very happy to say its all working extremely well using a combination of the lynx application to record keystrokes into a batch file and then production of a cron job. At 01:00 hrs the security camera LED starts flashing and at 05:00 the LED turns off.  This process will allow me to do much more automation with application and I greatly appreciate the help and guidance you all you have given me with particular thanks to Wobblybob for pointing out the lynx application.

Best Regards
Lenscom

---


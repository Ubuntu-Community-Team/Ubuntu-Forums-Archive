---
title: "Content Filter That Support Exceptions"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by tmoreland on 2008-01-02
I have been playing with Dansguardian a bit and reading about many of your experiences with it; however, I haven't found any discussions about allowing certain exceptions.

I want to configure a dedicated proxy server that will block everyone in the household but at different levels.  For example, with no authentication I want all "inappropriate" content blocked but when authenticated and part of the "adults" group, allow porn.  Most of my friends and family with kids support the idea of blocking their kids but they themselves don't want to be blocked (on the other hand, some wives love the idea of their husbands having no access to porn).  ...and no, I'm not trying to give myself access to porn... :---)

So, has anyone worked on this?  Any assistance would be greatly appreciated!

Troy

---

### Post by jmc1024 on 2008-01-02
Troy,
Look into squidGuard.  It plugs into squid much like dansguardian does.  With squidGuard it is quite easy to setup an installation doing just what you want.  You can find squidGuard in the repos as well as at squidguard.org.  
Here's an example config that could get you started (adults can view everything except porn, for everyone else porn, violence & warez are blocked):
acl {
     adults {
         pass !porn all
         redirect [http://localhost/cgi/blocked?clientaddr=%a&clientuser=%i&clientgroup=%s&url=%u](http://localhost/cgi/blocked?clientaddr=%a&clientuser=%i&clientgroup=%s&url=%u)
     }
     default {
         pass !porn !violence !warez all 
         redirect [http://localhost/cgi/blocked?clientaddr=%a&clientuser=%i&clientgroup=%s&url=%u](http://localhost/cgi/blocked?clientaddr=%a&clientuser=%i&clientgroup=%s&url=%u)
     }
} 
The people on the squidGuard maillist can answer all your specific questions.
Regards,
Mark

---

### Post by tmoreland on 2008-01-02
I did find this helpful little forum article.  I haven't tried it yet but it looks promising:

The newer version of Dansguardian will do ACLS.  It takes some effort to
setup.

In the dansguardian.conf file you add these two lines:
filtergroups = 2
filtergroupslist = '/etc/dansguardian/filtergroupslist'

In the filtergroupslist you add your usernames and the filter they
belong to:
abollinger=filter2
acicalla=filter2
aexter=filter2
agelsey=filter3

I make my most restrictive list filter1, because that's the fall back
for any name not found in the filtergrouplist.

You then create a dansguardian.conf file for each filter group. Called
dansguardianf1.conf, dansguardianf2.conf, etc.

In each filter configuration file, you add the standard config
information, but point to different files:
The shared files I have all named the same, filter specific files end in
the filter number.

bannedphraselist = '/etc/dansguardian/bannedphraselist2'
weightedphraselist = '/etc/dansguardian/weightedphraselist2'
exceptionphraselist = '/etc/dansguardian/exceptionphraselist'
bannedsitelist = '/etc/dansguardian/bannedsitelist2'
greysitelist = '/etc/dansguardian/greysitelist'
exceptionsitelist = '/etc/dansguardian/exceptionsitelist'
bannedurllist = '/etc/dansguardian/bannedurllist'
greyurllist = '/etc/dansguardian/greyurllist'
exceptionurllist = '/etc/dansguardian/exceptionurllist'
bannedregexpurllist = '/etc/dansguardian/bannedregexpurllist'
bannedextensionlist = '/etc/dansguardian/bannedextensionlist2'
bannedmimetypelist = '/etc/dansguardian/bannedmimetypelist2'
picsfile = '/etc/dansguardian/pics'
contentregexplist = '/etc/dansguardian/contentregexplist'

---


---
title: "Apache woes"
date: 2011-07-14
forum: New to Ubuntu
---

### Post by BUTTS on 2011-07-14
Hi folks. Bit of a novice here - Please can you help? I am developing some web pages with possibly some cgi scripts. I want to test them on my pc which I have Apache 2 running on. So I am making web pages on the same pc as Apache is on. Ok, I remember years ago doing this on a windows machine and simply placing the web pages in a folder somewhere in within apache and placing perl scripts in the cgi bin. Easy peasy. The Ubuntu docs say that I should simply do the same with var/www folder. But I cannot get write permission to do that. I have installed Filezilla and thought it might be a good way to do things since this is how I will upload my pages anyway. But it asks for host (which I presume is localhost). Then Username, and password. These two I am assuming there may be some default username and password. If there is - what are they? Lastly I presume it is port 80. Apache is running by the way. I have been trawling the web for answers, but I seem to be getting just confused. Any help would be appreciated.

Thanks,
        Butts.

---

### Post by GWBouge on 2011-07-14
Yes, it's listening on port 80.  Depending on your ISP, users may not be able to see the page from the outside world, but just for local testing it's fine.

Your /var/www/ is writable by root.  If you're editing on the same machine that's hosting the server, you could open up nautilus as root (gksu nautilus) and edit them right there, but one accidental click/delete could really screw things up.  Or edit the pages somewhere else and 'sudo cp' them to that directory.

Something else you can do would be to make a folder you have access to as a user (/home/user_name/public_html, for instance), and have /etc/apache2/sites-available/default point to that instead of /var/www.

There's a few options, most of which I probably don't know, but this is a start.

---

### Post by BUTTS on 2011-07-14
Thank you. I will try that.

---


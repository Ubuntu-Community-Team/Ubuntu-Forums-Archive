---
title: "Real time output from php script on unbuntu"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by AlistairH on 2010-10-19
This is more likely to be a PHP issue, rather than a Ubuntu one, but as it occured when I switched to a Ubuntu LAMP server I thought I'd post it here just in case.

I developed a PHP script that downloaded numerous files from an Internet site. It was run from an internal site hosted on SMEServer.

The script was designed to write the name of the file to screen on successful download and, unexpectedly, when I first ran it on SMEServer, each line was displayed in the webpage as the script progressed.

When I switched to Ubuntu, the behaviour was as I initially expected. i.e. the details wouldn't appear until the script had finished.

I quite liked the unexpected behaviour under SMEServer and wouldn't mind getting it back under Ubuntu.

As I said earlier, I'm sure this must be a PHP issue, and if any one is able to point me in the right direction I'd be grateful. Not to worry if not.

---

### Post by robsoles on 2010-10-19
Hi, my memory of doing that sort of stuff using the Apache setup is hazy but basically you need the buffer to output from the server to the browser while the script is still executing.

The default behaviour is to 'hang on' to the output till the final instruction/byte of the source file has been processed but there are buffer controls to override that so as to have a 'live update' style output.

[http://php.net/manual/en/book.outcontrol.php](http://php.net/manual/en/book.outcontrol.php) looks to me like it has the commands you need listed.

---

### Post by AlistairH on 2010-10-24
Thanks for getting back robsoles.

Since my posting, I had investigated those but they require putting the commands in the php script.

The difference in behaviour seen between running on SMEServer and subsequently UBuntu Server, was for exactly the same script with no modifications. Presumably then, the setting concerned must be a global setting either in php.ini or at the Apache2 level.

I haven't, as yet, identified what it is.

---

### Post by robsoles on 2010-10-25
Welcome.

It should be in php.ini then, and a comparison of the contents of the php.ini file from SMSServer and Ubuntu Server will probably reveal it.

Personally I'd make the script (.php files) take care of it so it is portable without asking whatever new host to modify their php.ini file and risking making something else on the server break.

If any script in any site reliant on the server modifies headers after beginning output it will err after the change to the php.ini file - My favorite CMS wouldn't run successfully for instance.

---

### Post by AlistairH on 2010-10-25
All very valid point robsoles.

Unfortunately, a comparison of php.ini files isn't possible as I wiped the SMEServer when installing Uuntu Server.

It's not a major issue. I was more curious than anything, but having seen it in action, I quite liked getting the 'instant' feedback.

Thanks for getting back to me.

---


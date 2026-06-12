---
title: "permissions for Cache_lites cacheDir a permissions problem I think"
date: 2009-06-15
forum: New to Ubuntu
---

### Post by bennychidge on 2009-06-15
Hi all

I am in the wonderful world of devloping on windows and then going live on Ubuntu (next upgrade isnt a windows one) and I have hit what looks like a permissions issue.

I am using the fantastic cache_lite from PEAR with php and on my dev setup i can specify a cacheDir by the using the following options

```

require_once 'Cache/Lite/Output.php';
	$options = array(
	'cacheDir' => '../cache', 
	'writeControl' => 'true',
	'readControl' => 'true',
	'fileNameProtection' => false,
	'readControlType' => 'md5'
	);
$cache = new Cache_Lite_Output($options);
```

this then stores the cache files outside of the web server in the folder "../cache".

But on Ubuntu this wont work, so for the moment I have just removed 

```
'cacheDir =>'../cache',
``` as I am tired and bored in the knowledge that this is really easy but I dont understand and have gone onto more productive things.

So for the moment on Ubuntu acording to a popular search engine it now defaults to '/tmp' for caching and is working even if not as intended.

But it seems whilst reading my book I need to:

"Note that the cacheDir directory we specify must be one to which the script has read and write access:"

Can some explain to me in laymans terms how I would go about giving the script (I presume Cache/Lite/Output.php) read and write access to my ../cache directory.

And if in Ubuntu do I have to specifiy an absolute path to the cache directory or can i just use the relative one I am already using?

Many Thanks in advance for any pointers, and I look forward to laughing at this in the future.

A few things, I know how to give permisions to a user/group but how to do it for a php file?

Im lost......

Thanks

---

### Post by bennychidge on 2009-06-20
crash, bang, wallop - bump!

No one with help on this one...? Thanks

---

### Post by Mornedhel on 2009-06-20
Hi,

You don't give rights to a script or an application, instead you give rights to the user the application is running as. For instance, if I create a bash script foo.sh and run it with ./foo.sh, it will have the same rights I have.

You can use sudo to run things as a different user, This is probably useless to you since you can't really enter a password for PHP scripts, but I thought I'd mention it since it can be useful in the general case.

setuid and setgid, set via the chmod command (+s for setuid), allow the script to run with its owner's rights even when started by someone else. This is useful for advanced situations.

In your case it's probably all a matter of finding out who can access ../cache properly and chown'ing the script to that user (root, apache... I am not a network administrator or a Web developer, so I can't really help you further).

---

### Post by bennychidge on 2009-06-22
yes it was permissions issue but also an absolute url issue for the cahce directory.

Ended up chmod 777'ing the cache directory which worked a treat

found this very useful (as well as here)

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)


thanks

---


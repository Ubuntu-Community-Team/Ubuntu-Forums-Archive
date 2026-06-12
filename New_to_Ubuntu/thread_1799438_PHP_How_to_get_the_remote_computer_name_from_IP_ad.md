---
title: "PHP: How to get the remote computer name from IP address"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by honeybear on 2011-07-07
Hello, 

Would somebody know how to do that under PHP ? 

I found some solution with google but under PHP it is not so easy... 

is there something better than this? Where is the provider also? 
> $servername = gethostbyaddr($_SERVER['REMOTE_ADDR']);


is that better? 
> 
>> getenv('COMPUTERNAME')
>> $_ENV['COMPUTERNAME']
>> $_SERVER['COMPUTERNAME']


Regards

---

### Post by doas777 on 2011-07-07
I believe we discussed this last week..

the gethostbyaddr is prolly your best bet, and that about as simple a call as can be. 

as for the provider, that is not somthing you can easily determine by packet or session/request info, but you can look it up in the whois database, using somthing like this:
[http://www.phpwhois.org/](http://www.phpwhois.org/)
('php whois' turned up a lot on google, so there may be alternatives that suite your needs more specifically).

---

### Post by honeybear on 2011-07-07
> **doas777 said:**
> I believe we discussed this last week..

the gethostbyaddr is prolly your best bet, and that about as simple a call as can be. 

as for the provider, that is not somthing you can easily determine by packet or session/request info, but you can look it up in the whois database, using somthing like this:
[http://www.phpwhois.org/](http://www.phpwhois.org/)
('php whois' turned up a lot on google, so there may be alternatives that suite your needs more specifically).

And what is this ? Does it do somthing right or it forces things? 

```

function getRealIpAddr()
{
    if (!empty($_SERVER['HTTP_CLIENT_IP']))   //check ip from share internet
    {
      $ip=$_SERVER['HTTP_CLIENT_IP'];
    }
    elseif (!empty($_SERVER['HTTP_X_FORWARDED_FOR']))   //to check ip is pass from proxy
    {
      $ip=$_SERVER['HTTP_X_FORWARDED_FOR'];
    }
    else
    {
      $ip=$_SERVER['REMOTE_ADDR'];
    }
    return $ip;
}
```

---

### Post by honeybear on 2011-07-07
OK I have it.

# 
```
function getRealIpAddr() {
  if(!empty($_SERVER['HTTP_CLIENT_IP'])) {
    $ip=$_SERVER['HTTP_CLIENT_IP']; // share internet
  } elseif(!empty($_SERVER['HTTP_X_FORWARDED_FOR'])) {
    $ip=$_SERVER['HTTP_X_FORWARDED_FOR']; // pass from proxy
  } else {
    $ip=$_SERVER['REMOTE_ADDR'];
  }
  return $ip;
}
$ipreal = getRealIpAddr(); // Get the visitor's IP
 
$ip = $_SERVER['REMOTE_ADDR']; // Simple version
```

And now how to get the computername and username from the remote_addr?

---

### Post by lisati on 2011-07-07
> **doas777 said:**
> 
the gethostbyaddr is prolly your best bet, and that about as simple a call as can be. 
I agree, this is probably the easiest.

There are options for learning stuff about the provider. One option is the SEM-ASN-ORIGIN list described here: [http://spameatingmonkey.com/usage.html#asn](http://spameatingmonkey.com/usage.html#asn)

Learning the user? I'm not sure about that if it involves someone else's network, because it raises privacy issues that might require a subpoena.

---

### Post by doas777 on 2011-07-07
> **honeybear said:**
> OK I have it.

# 
```
function getRealIpAddr() {
  if(!empty($_SERVER['HTTP_CLIENT_IP'])) {
    $ip=$_SERVER['HTTP_CLIENT_IP']; // share internet
  } elseif(!empty($_SERVER['HTTP_X_FORWARDED_FOR'])) {
    $ip=$_SERVER['HTTP_X_FORWARDED_FOR']; // pass from proxy
  } else {
    $ip=$_SERVER['REMOTE_ADDR'];
  }
  return $ip;
}
$ipreal = getRealIpAddr(); // Get the visitor's IP
 
$ip = $_SERVER['REMOTE_ADDR']; // Simple version
```And now how to get the computername and username from the remote_addr?


well
```
$srvName = [gethostbyaddr]("http://ro.php.net/manual/en/function.gethostbyaddr.php")($ip)
``` will get you the dns name of the client.
then you can do a whois on the srvName to get the hosting info. 

as for username, that is not possible, unless you are using an login/authentication system and giving them a name. the name of the user interactively logged into a PC is not passed by the browser and should not be externally visible. MS IE does "Integrated Authentication" whereby the browser submits the logged in credentials with teh request, but that is only valid for IIS servers and IE clients. in some limited sense, you may be able to get some info from '[finger]("http://pear.php.net/package/Net_Finger/docs/latest/Net_Finger/_Net_Finger-1.0.1---Finger.php.html")', but the user has to be listed in a finger server to be of any use. no php app you could write would be capable of determining the username I have used to login to my desktop.

---

### Post by wojox on 2011-07-07
Doesen't the *php_uname* function work anymore?

---

### Post by mikejonesey on 2011-07-07
the computer name is also not possible through php, which is a server side script, resolving the ip will not filter back to the user's pc in 98% of cases as most of us don't have a fixed ip and even if we did it would resolve to the isp in most cases...

for example your php prog would be able to trace me currently to... 82.44.31.??? which traces back to virgin media...

when i send a request now it is going to the router, the router (which is logged onto virgin) sends a request to virgin, virgin then makes a request to the net on my behalf and sends the data back to me... virgin at no point passes on and info about my machine or current dynamic ip with them... so you can get the virgin connection point name that me and i guess hundreds are using, but never my computer name...

however what you could do is place a bit of client side script (js+ajax) to feed back computer name, through activex controls alot more (ie)... you can then associate and save stats...

---

### Post by doas777 on 2011-07-07
> **wojox said:**
> Doesen't the *php_uname* function work anymore?
php_uname appears to be a version of unix 'uname', but via php, so it does not return the users name, but the kernel name/ver of the server. 

[http://php.net/manual/en/function.php-uname.php](http://php.net/manual/en/function.php-uname.php)

---

### Post by wojox on 2011-07-07
> **doas777 said:**
> php_uname appears to be a version of unix 'uname', but via php, so it does not return the users name, but the kernel name/ver of the server. 

[http://php.net/manual/en/function.php-uname.php](http://php.net/manual/en/function.php-uname.php)

Yeah, I use to use it many moons ago. :P 
Different switches for it.
PHP does a lot of changing. Didn't know if it was still around.

I agree, username would be a major security risk outside a Lan. Internally you could probably do it.

---


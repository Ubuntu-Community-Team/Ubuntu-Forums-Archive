---
title: "Crontab a PHP script? or Apache?"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by steve1978 on 2010-11-18
Hi. 
 
I am a novice.... total novice. a friend made me a php script that works a treat for what i want it to do. it contains a little bit of cURL and stuff, not sure if thats relevent.
 
I would like to set the script to run every 20 minutes. initially i though i would use cron job. I have set it all up to run but when i trid to run the script manually i got error messages...
./turf.php: line 1: ?php: No such file or directory
./turf.php: line 2: syntax error near unexpected token `('
./turf.php: line 2: `$headers = array();'
 
now i know the script works as i saw him manually run it using xampp. 
 
What is the best method to get the script to automate on every 20 mins on my Ubuntu PC, (10.04 LTS)
 
Thanks for any help

---

### Post by cariboo on 2010-11-18
Are you using XAMPP or LAMP, because the two are setup totally different.

---

### Post by alienprdkt on 2010-11-18
make sure you have php-cli

sudo apt-get install php5-cli

then what you will do is:

crontab -e

20 * * * * /path/to/script


to quit crontab enter:

:wq

you should see your script in the crontab list:

crontab -l 

hope this helps

---

### Post by steve1978 on 2010-11-18
> **alienprdkt said:**
> make sure you have php-cli
 
sudo apt-get install php5-cli
 
then what you will do is:
 
crontab -e
 
20 * * * * /path/to/script
 
 
to quit crontab enter:
 
:wq
 
you should see your script in the crontab list:
 
crontab -l 
 
hope this helps
Hi,
 
Thanks for the details. i tried these and had a couple of issues. i didnt create this script a friend did it and i watch him run it and it worked and i think he said he was using xampp.
 
i followed your instructions, i am using putty. i ran the crontab -l and the script ran
root@pc:/etc# crontab -l
# m h dom mon dow command
20 * * * * /etc/turf.php
 
 
then it went back to the prompt, i checked to see if it had worked and it hadn't the scripts intention is to create an auto bump post on a forum thread. 
I added this to the crontab:
20 * * * * /etc/turf.php >> /var/log/turf.log
 
 
but no log file was created. any suggestions much appreciated. 
thanks
 
Edit interestingly if i do this 
/etc# ./turf.php
 
i get this
./turf.php: line 1: ?php: No such file or directory
./turf.php: line 2: syntax error near unexpected token `('
./turf.php: line 2: `$headers = array();'
 
Also, do i need to install anything to allow cURL to run?

---

### Post by alienprdkt on 2010-11-18
you can try 


sudo /etc/init.d/cron restart

then wait and see if it runs in the next 20 mins...

also to see if it ran:

20 * * * * /path/to/script 

date +"%D %r 'echo Cron completed'" >> /tmp/cron_job.log


that way you can tell if it actually ran

---

### Post by trentscott on 2010-11-18
> i get this
./turf.php: line 1: ?php: No such file or directory
./turf.php: line 2: syntax error near unexpected token `('
./turf.php: line 2: `$headers = array();'

Also, do i need to install anything to allow cURL to run?

This sounds like a syntax error within the PHP file itself. It's hard to diagnose without (a) looking at the source code of the file you're trying to run, and (b) knowing what PHP version/environment you have setup.

---

### Post by steve1978 on 2010-11-18
This is the code it is for designed to log in to a forum and bump a thread. the idea is you post your code and friends can add it. i am just looking to automate it ;)
 
my linux pc says this:
[SIZE=2]Configuration File (php.ini) Path [/SIZE][SIZE=2]/etc/php5/apache2 [/SIZE]
any other info i can give will be appreciated.
thanks
 
```

<?php
$headers = array();
$headers[] = 'Connection: Keep-Alive'; 
$headers[] = 'Content-type: application/x-www-form-urlencoded;charset=UTF-8'; 
$headers[] ='Host: turfwarsapp.com';
$headers[] ='Connection: Keep-Alive';
$headers[] ='Cache-Control: no-cache';
$user_agent = 'Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.0.3705; .NET CLR 1.1.4322; Media Center PC 4.0)';
#$url="http://turfwarsapp.com/login?redir=http://turfwarsapp.com/forum/171/THREAD-ID/http://turfwarsapp.com/forum/171/THREAD-ID";
$url="http://turfwarsapp.com/login";
$turfurl="http://turfwarsapp.com/forum/";
$turfwars="login[name]=USERNAME&login[pass]=PASSWORD&action=login";
$ch = curl_init($turfurl);
curl_setopt($ch, CURLOPT_POST ,0);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION ,1);
curl_setopt($ch, CURLOPT_HEADER ,1); // DO NOT RETURN HTTP HEADERS
curl_setopt($ch, CURLOPT_RETURNTRANSFER ,1); // RETURN THE CONTENTS OF THE CALL
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers); 
curl_setopt($ch, CURLOPT_HEADER, 1); 
curl_setopt($ch, CURLOPT_USERAGENT, $user_agent); 
curl_setopt($ch, CURLOPT_COOKIEJAR, '/tmp/cookies.txt');
curl_setopt($ch, CURLOPT_COOKIEFILE, '/tmp/cookies.txt');
$resp = curl_exec($ch);
$ch = curl_init($url);
curl_setopt($ch, CURLOPT_POST ,1);
curl_setopt($ch, CURLOPT_POSTFIELDS ,$turfwars);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION ,1);
curl_setopt($ch, CURLOPT_HEADER ,1); // DO NOT RETURN HTTP HEADERS
curl_setopt($ch, CURLOPT_RETURNTRANSFER ,1); // RETURN THE CONTENTS OF THE CALL
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers); 
curl_setopt($ch, CURLOPT_HEADER, 1); 
curl_setopt($ch, CURLOPT_USERAGENT, $user_agent); 
curl_setopt($ch, CURLOPT_COOKIEJAR, '/tmp/cookies.txt');
curl_setopt($ch, CURLOPT_COOKIEFILE, '/tmp/cookies.txt');
$resp = curl_exec($ch);
echo $resp;
#echo"<pre>";
#print_r($_COOKIE,true);
#echo"</pre>";
#exit();
&#12288;
$headers[] ='Accept-Language: en-gb';
$headers[] ='Referer: http://turfwarsapp.com/forum/171/32855819/2';
$headers[] ='POST /api/forum/create HTTP/1.1';
$headers[] ='Content-Type: application/x-www-form-urlencoded';
$headers[] ='Cookie: __utma=240852486.24776342.1290086274.1290086274.1290086274.1; __utmb=240852486.16.10.1290086274; __utmz=240852486.1290086274.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none); __qca=P0-16577486-1290086274445; S=ZMElGSt3li7vWVOq7OwIJlqN-T4; __utmc=240852486';
$ch = curl_init('http://turfwarsapp.com/api/forum/create');
$args['enid']='32855819';
$args['fp']['body']='bump!';
$args['fp']['title']=NULL;
$post = json_encode($args);
$post = 'enid=32855819&fp[body]=bump';
$post = 'enid=32855819&fp%5Bbody%5D=bump!';
$headers[] = 'Content-Length: '.strlen($post);
curl_setopt($ch, CURLOPT_POST ,1);
curl_setopt($ch, CURLOPT_POSTFIELDS ,$post);
curl_setopt($ch, CURLOPT_FOLLOWLOCATION ,1);
curl_setopt($ch, CURLOPT_HEADER ,1); // DO NOT RETURN HTTP HEADERS
curl_setopt($ch, CURLOPT_RETURNTRANSFER ,1); // RETURN THE CONTENTS OF THE CALL
curl_setopt($ch, CURLOPT_HTTPHEADER, $headers); 
curl_setopt($ch, CURLOPT_HEADER, 1); 
curl_setopt($ch, CURLOPT_USERAGENT, $user_agent); 
curl_setopt($ch, CURLOPT_COOKIEJAR, '/tmp/cookies.txt');
curl_setopt($ch, CURLOPT_COOKIEFILE, '/tmp/cookies.txt');
$resp = curl_exec($ch);
echo '<div style="padding:10px;background:#456;color:#FFF">'.$resp.'</div>';
&#12288;
/*
POST /api/forum/create HTTP/1.1
Accept-Language: en-gb
Referer: http://turfwarsapp.com/forum/171/32855819/2
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip, deflate
User-Agent: Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 5.1; Trident/4.0; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04506.30; .NET CLR 3.0.4506.2152; .NET CLR 3.5.30729; .NET4.0C; .NET4.0E)
Host: turfwarsapp.com
Content-Length: 32
Connection: Keep-Alive
Cache-Control: no-cache
Cookie: __utma=240852486.24776342.1290086274.1290086274.1290086274.1; __utmb=240852486.16.10.1290086274; __utmz=240852486.1290086274.1.1.utmcsr=(direct)|utmccn=(direct)|utmcmd=(none); __qca=P0-16577486-1290086274445; S=ZMElGSt3li7vWVOq7OwIJlqN-T4; __utmc=240852486
*/
&#12288;
?>

```

---

### Post by alienprdkt on 2010-11-19
> **steve1978 said:**
> 
 
Also, do i need to install anything to allow cURL to run?

sudo apt-get install php5-curl

sudo /etc/init.d/apache2 restart

---


---
title: "wget calling php request - creates a html file in my server root"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by bennychidge on 2009-05-22
Hi 

I am new to Ubuntu and Wget, and newish to php.

I have setup a wget in my crontab

```
*/45 * * * * wget http://www.randomblahblah.com/?cron=true
```

The php code checks for this parameter and then does something...

The problem I have is that this is creating a file index.html?cron=true every 45 mins in my servers root.

Any ideas why this would be? 

I would ideally like this not to happen -is this normal for wget? 

Thanks

P.s thats an empty index.html file!

---

### Post by bennychidge on 2009-05-22
sorry found out how by suprise suprise reading the manual! (EDIT NO I HAVENT ITS STILL HAPPENING!!)

```

wget -q http://www.randomblahblah.com/?cron=true >/dev/null 2>&1
```

the 
```
-q
``` 
means quiet

and the 
```
>/dev/null 
```
means redirect to dev/null (black whole)

and the
```
2>&1
```
put  STDERR into STDOUT then into the black whole

(isnt the internet great)

---

### Post by bennychidge on 2009-05-22
Ok bit ahead of myself - that hasnt worked?

I am still getting index.html?cron=true empyt file in my server root


Any ideas? Please help

---

### Post by mrog on 2009-05-22
Put the URI in quotes:

wget -q "http://www.randomblahblah.com/?cron=true" >/dev/null 2>&1

---

### Post by kpkeerthi on 2009-05-22
What happens when you enter the url in firefox? The same will happen with wget, except that the webpage will be saved locally.

---

### Post by bennychidge on 2009-05-22
the "" havent worked

I thought or got the impression that sending the wget to dev/null would stop this from happening?

The ?cron=true is being used in my php script to access an API using cURL so that the information is checked every two minutes rather than everytime the page is loaded.

Any Ideas how I can do this so the empty file isnt saved in my root?

---

### Post by Celauran on 2009-05-22
I'm not really clear on what you're trying to do, but the whole purpose of wget is to get a file. I suppose you could have a cron job run and delete the file a few minutes after the wget job, but that hardly seems like the right solution. Again, depending on what you're trying to do, you may have better luck with Python's urllib.

---

### Post by bennychidge on 2009-05-22
I have found the following to work as I need it to

```

wget --delete-after http://www.blahblah.com/?cron=true
```

the php I am using is

```

$pickupcron = true;
if ( $pickupcron && $_REQUEST['cron'] == 'true' ) {
	//perfom a cURL request to an API
	exit;
}

```

This means that I can request the xml/Json file and store it in my db with cron rather than with every page load

Thanks for the help

---


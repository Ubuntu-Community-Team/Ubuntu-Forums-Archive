---
title: "Recover of deleted file"
date: 2011-04-09
forum: New to Ubuntu
---

### Post by wholein1 on 2011-04-09
Hello, 
 
I am a student that has project due in a few weeks and trying to learn linux basic commands and then completeing all the requirements is to say the least a challenge. I have some how [COLOR=black]deleted a file (default) that belongs in the sites available[/COLOR]. I am not even sure if the ubuntu forumcan help me, but I thought I would give it a try. Can anyone give me some simple help to know how to recover the default file, or replace? What do I need to do?
 
Thank you

---

### Post by Fraoch on 2011-04-09
> **wholein1 said:**
> I have some how [COLOR=black]deleted a file (default) that belongs in the sites available[/COLOR].

Could you re-word that?  I'm not sure I understand.

Do you mean you've deleted a system file, not one you created?  For a newbie, that takes some doing - generally you can't do this by mistake, which is one of the advantages of Linux.

If you've deleted a file you created, i.e. one located in your "home" directory, it will first go into the trash.  Your trash icon should appear to have something in it, like Windows.  Just restore it from there.

Do you have a trash icon either on your desktop or in your panel bar?  If not, you can add it to the panel bar by right-clicking on your panel, selecting "Add to Panel" and the Trash icon.

If it was a file that went to trash and you deleted it from the trash or emptied the trash then yes, it is gone.

But deleting a file you did not create, one that was supplied with the system and is not in your home directory, requires some very specific commands.  Generally the system will not let you do this.  You have to do this from the terminal using some commands.  It can also be done graphically, using even more obscure commands from the terminal (and even then, these files go to another trash bin).  Each method will ask you for your password first.  In short, you simply can't do this by accident.  In fact you should not be able to move files either, at least not by accident.

It's much more likely you did something else - reconfigured something, for example, and can't get the original configuration back.  This may make something disappear.

How do you know a file was deleted?  Do you have an idea what it might have been?  What happened?

---

### Post by wholein1 on 2011-04-09
I deleted the default file in sites-available and I need to undelete it I was removing a file and typed the wrong file name in when using the rm command. It is a non gui and we are using command line to manipulate the unbuntu and apache

---

### Post by mcduck on 2011-04-09
If you used rm, then the file really is gone and can't be recovered.

Lucky for you, I also happen to run Apache and haven't touched the default site configuration (as I'm using custom site instead), so here's the contents of that file so you can create a new one:

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

---

### Post by wholein1 on 2011-04-09
I am new to the apache and linux. What is the best way to get that nformation into a file. Is there a comand way of doing it or would it be better to creat a file and hand type the code?

---

### Post by Fraoch on 2011-04-09
> **wholein1 said:**
> I am new to the apache and linux. What is the best way to get that nformation into a file. Is there a comand way of doing it or would it be better to creat a file and hand type the code?

The preferred command-line editor is nano - type "sudo nano /etc/apache2/sites-available" to create the file as root if it doesn't exist, or to edit it.

nano does have cut-and-paste - even better in your case, you can insert a whole file.  Save mcduck's text as whatever you want and in nano press CTRL + R (see the pointers at the bottom of the nano screen), then type in the path to the text.  Almost as easy as a GUI.

nano tends to grow on you.  It's simple but pretty powerful.:)

---


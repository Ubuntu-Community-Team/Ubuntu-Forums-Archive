---
title: "Welcome to Nginx index.html"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by ex-para on 2010-04-05
As I only have only the one website I have been able to put the details of the site into /var/www/nginx-default but now how do I get rid of the Welcome to Nginx index.html I have tried all ways to do this with no success.

---

### Post by r-senior on 2010-04-05
What's the name of your start/home page for the site? Is it not index.html?

What webserver are you using?

---

### Post by s_ø on 2010-04-05
What exactly are you talking about? What are you trying to do - edit a html file? delete a html file? setup your nginx server?

---

### Post by ex-para on 2010-04-05
I am not quite sure about your question but I am using Nginx and ngnix has a Welcome to ngnix page when you have installed to show it is working. If like me you only have one site you can remove index.html which has the welcome and replace it with an index.html that has my website details in it. I can add the html I need but I cant delete or rename the index.html I need to get rid of.
Yes I am setting up my server and I do need to delete edit, delete or rename a html file. 
Thanks for the replies.

---

### Post by sandyd on 2010-04-05
> **ex-para said:**
> As I only have only the one website I have been able to put the details of the site into /var/www/nginx-default but now how do I get rid of the Welcome to Nginx index.html I have tried all ways to do this with no success.

```

cd  /srv/http/[I]nginx
[/I]
```
slap everything in there.

---

### Post by ex-para on 2010-04-06
Thanks for the reply but this is all I get.
acme@acme-laptop:~$ cd  /srv/http/nginx

bash: cd: /srv/http/nginx: No such file or directory

acme@acme-laptop:~$ sudo cd  /srv/http/nginx

[sudo] password for acme: 

sudo: cd: command not found

acme@acme-laptop:~$

---

### Post by ex-para on 2010-04-06
How would go about this,I found it in my search for information but I don't know how to follow it up. 



If you only have the one domain, a simple way would be to delete or rename
the nginx/html directory and then create a symbolic link to nginx/html from
your doc root.

 

# mv  /path/to/nginx/html /path/to/nginx/html.bak

 

# ln -s /path/to/doc/root /path/to/nginx/html

---

### Post by s_ø on 2010-04-06
When you go to [http://localhost](http://localhost) the page with "Welcome to nginx!" is displayed, right?
The path to that file is (on a fresh install) **/var/www/nginx-default/index.html**.
**1**. You can replace that file with your own index.html file.
**2**. You can make a symbolic-link called index.html that points to your own file.
**3**. You can edit the virtualhost documentroot to point to your file. (I would do it this way)

Assuming you have a directory called **/var/www/my-www** and a file called **my-index.html** in that directory.
**1**. Open a terminal
Replace nginx default index with your my-index.html
```
sudo cp /var/www/my-www/my-index.html /var/www/nginx-default/index.html
```**2**. Open a terminal
delete nginx default page.
```
sudo rm /var/www/nginx-default/index.html 
```Make a symbolic link to your my-index.html
```
sudo ln -s /var/www/my-www/my-index.html /var/www/nginx-default/index.html 
```**3**. Open a terminal
Backup nginx default virtualhost.
```
sudo cp /etc/nginx/sites-available/default /etc/nginx/sites-available/default_backup
```Open nginx vitualhost settings.
```
sudo nano /etc/nginx/sites-available/default 
```Change
```
location / {
                root   /var/www/nginx-default;

```to
```
location / {
                root   /var/www/my-www;

```

---

### Post by ex-para on 2010-04-07
If I don't get it working this time I never will as I have been trying on and off for about a year, the website that I built myself six years ago with the help of w3wchools is hosted by a paid host but it should be OK if I can host it myself as it is just to show some buyers abroad what I have and they are on the same zone time which helps. I am going to delete the whole thing, hard drive the lot and start again as it is a bit messed up with trying this and that, this will be about the tenth time.
Thank you very much for the information.

---

### Post by s_ø on 2010-04-07
Remember to restart/reload the server for config changes to be applied.

It shouldnt be necesary to reinstall to get a working http server.
But if you do and install nginx, use the one from the repository
```
sudo apt-get install nginx
```or you can install apache (with php/mysql)
```
sudo tasksel install lamp-server
```Both options will give you a working server where all you need to do is copy you site to a directory inside /var/www.
Then follow the instructions in point 3 in the post above.
For apache, substitute 'nginx' with 'apache2' and look for ```
DocumentRoot /var/www
```

---

### Post by ex-para on 2010-04-08
Things are not going to good as I am unable to get past the first command 

acme@acme-laptop:~$ sudo cp /var/www/my-www/my-index.html /var/www/nginx-default/index.html

cp: cannot stat `/var/www/my-www/my-index.html': No such file or directory

acme@acme-laptop:~$ 

this is there  /var/www/nginx-default/index.html and I have made my ( 
my-index.html ) with my website details in it an at the moment it is in home folder. Should I put it in 
/var/www

---

### Post by s_ø on 2010-04-08
cp is a copy command. You can only copy files that exists.
the /my-www/my-index.html was an example.

I think the easiset way is to delete the index.html file inside /var/www/nginx-default.
When you have done that copy your entire site (including all subdirectories) to /var/www/nginx-default.

Then open a browser and see what happens at [http://localhost](http://localhost)

---

### Post by ex-para on 2010-04-09
I can move files into /var/www/nginx-default but removing or deleting from /var/www/nginx-default is something else as I get 
You do not have the necessary permissions to save the file.
I tried this but no good 
gksudo gedit /etc/apt/sources.list

---

### Post by s_ø on 2010-04-09
why would you edit the sources.list? It has nothing to do with your http server.
To delete a file owned by root you would use **sudo** before the command.
I would recommend you read about terminal commands [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
And file permissions [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

If you have copied your site to the directory **/var/www/nginx-default **you can access it from your browser.
What is the name and path of the index page you want to use?

---

### Post by ex-para on 2010-04-11
[SOLVED] Could not save? 

I thought this might have helped me.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

How do I fix this?

*

Re: Could not save? 

Code:
gksudo gedit /etc/apt/sources.list
now you have the permission

Welcome to nginx is still showing when I go to localhost.
I named web details my-index.html and if the location is the path it is  /var/www/nginx-default.

I have been this far before and could access welcome to nginx after configuring my hub with my external IP from a friends computer but I have never been able get rid of the welcome to nginx

---

### Post by s_ø on 2010-04-11
try to go to [http://localhost/my-index.html](http://localhost/my-index.html)
I really think you should read the links i gave you about file permissions and sudo.
sudo gives you root privileges for a specific task, such as starting the webserver, editing config files and so on.
gksudo is for graphical programs like gedit.
so if you wanted to edit /var/www/nginx-default/index.html in the editor gedit, you would use this command.
**gksudo gedit /var/www/nginx-default/index.html**

If [http://localhost/my-index.html](http://localhost/my-index.html) works, overwrite the default index with your own. Use the **mv** (move) command
sudo mv /var/www/nginx-default/my-index.html /var/www/nginx-default/index.html

---

### Post by ex-para on 2010-04-12
That worked great first time and for the first time I have got rid of welcome to nginx thank you very much. Now I have to configure my hub again. I will take your advice and study the file permissions and sudo now that I have seen how it works with them you have sent I have more idea about it.

---

### Post by s_ø on 2010-04-12
Good thing its working. If you got your problem solved, can you please mark the thread solved.
You should also check out the [Ubuntu Serverguide]("https://help.ubuntu.com/9.10/serverguide/C/index.html") There is a lot of good info on getting things up and running, unfortunately nothing about nginx.

---

### Post by masesaco on 2011-03-17
I got the same problem.
Everytime I wrote something on adress bar, got the message "welcome to nginx", and no results about my wanted search.
Tried also modify the :config of firefox, and got nothing.

And the solution was soooo easy.
Just did put mcafee to run, found 6 trojan, exploits, cleaned them, and the problem was completly solved... the old google search started to work automatically as before

---


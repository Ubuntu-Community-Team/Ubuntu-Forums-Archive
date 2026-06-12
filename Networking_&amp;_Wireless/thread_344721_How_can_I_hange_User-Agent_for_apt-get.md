---
title: "How can I hange User-Agent for apt-get?"
date: 2007-01-23
forum: Networking &amp; Wireless
---

### Post by mikuskuikku on 2007-01-23
Having problems with the a proxy at work and I need to get through it by changing the user-agent string.
The proxy lets me download from ftp without going through the proxy. But when downloading from http the proxy requires username/password.
I can get wget to work by changing the user-agent string, but I don't know where/how I should change the config so that apt-get or aptitude runs with a user-agent string.
When scanning my traffic with wireshark/ethereal it looks like my user-agent string is
```
Ubuntu APT-HTTP/1.3\r\n
```
I have tried to set
```
export http_proxy="http://[username]:[PW]@[IP]:[PORT]
```
Instead of " 403 Forbidden" the above setting results in "407 Proxy Authentication Required".
So http_proxy doesn't seem to be an alternative for me.
Changing user-agent string seems like a good idea.

Suggestions how I could change the user-agent string for apt-get?

---

### Post by jorno on 2007-09-10
I don't know if anyone still has this problem, but I found my solution in another post. (Read on -> You'll be able to manipulate your USER-STRING)

The steps mentioned here earlier are good and all, BUT if those of  you who's got this problem is in a Windows environment with a Microsoft ISA Proxy that need authentication, this is the solution that worked for me:

You need to install NTLMAPS.

[http://packages.ubuntu.com/feisty/web/ntlmaps](http://packages.ubuntu.com/feisty/web/ntlmaps)
* Go there, and download, either from within Firefox (if you manage to get Proxy working with Firefox - I did, but not apt-get or Synaptics or anything else).
* Download the package for ntlmaps (this is for Ubuntu Feisty)
* Start a terminal, find your downloaded package, and type:
*sudo dpkg -i ntlmaps_0.9.9.0.1-6_all.deb*
This should guide you trough the installation of the package...

BUT, my problems didn't stop there!
After, I had to edit /etc/ntlmaps/server.cfg manually.
( *sudo vim /etc /ntlmaps/server.cfg* )
Then I saw that the config-file was formatted with DOS (not UNIX), so I had to tell vim to convert it to UNIX-format. Do this in vim:
*:set fileformat=unix*
*:wq*
This should convert the file, and save it.
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 98), and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").

After those changes, restart ntlmaps:
*/etc/init.d/ntlmaps restart*

And point all your proxy-settings to: [http://127.0.0.1:5865](http://127.0.0.1:5865)

Make a file: */etc/apt/apt.conf*
Acquire::http::Proxy "http://127.0.0.1:5865";

And then try "*apt-get update*".

You could also insert this into:
System -> Preferences -> Network Proxy

And in Synaptics:
System -> Administration -> Synaptics -> Settings -> Preferences -> Network:
Manual proxy configuration:

127.0.0.1 port 5865 (no authentication)


This should do the trick! It did for me.. Please ask if there is something not clear yet, or if I should correct any of this. (Sorry, English is not my native tongue).

---

### Post by furtherdream on 2007-12-17
I also had to change some of the options:
Under the [CLIENT_HEADER] section, I had to comment out the first Accept and User-Agent part (Windows 9, and then uncomment the next part (Windows 2000 emulation).
Then I filled in "NT_HOSTNAME" (remembered what PC number this workstation had in Windows), and "NT_DOMAIN").
---------------------------------------------------------------------------------
I do as you said, but i don't understand the change above? My setting is below:
[COLOR="Red"]Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, application/vnd.ms-excel, application/msword, application/vnd.ms-powerpoint, */*^M
User-Agent: Mozilla/4.0 (compatible; MSIE 5.5; Windows 98)
NT_HOSTNAME:platform
NT_DOMAIN:asia[/COLOR]
BUT, i still can not passed the [Proxy Authentication], my firefox works well with the proxy setting. Can you give me some advice? Thanks.

---

### Post by furtherdream on 2007-12-17
I'm sorry, i just use ps -aux | grep ntlmaps and pstree | grep ntlmaps to check it, i found it does not run in background,and there is no error messages in my /var/log/messages. what's problem with it? i see the server.cfg file, it seems still is the DOS file format. Because i see there is still ^M in the end of each line. Is it the problem?

---

### Post by furtherdream on 2007-12-17
Hey, I just got access to internet with ISA Proxy, below is the message i got from [COLOR="Red"]http://www.tuxmachines.org/node/12889/print[/COLOR]

FYI
 kubuntu vs MS ISA Proxy ft apt-get
By Bezdomny
Created 01/25/2007 - 10:16

Recently I had to install an app on Kubuntu through apt but found that I was locked behind a MS ISA Proxy server at work. I read numerous articles and help responses in the forums that suggested adding a line to /etc/apt/apt.conf with the required proxy settings.

I added the regulatory Acquire::http::proxy [http://username:password@server](http://username:password@server) and nothing worked. It does not allow the use of the domain name\username combination. Neither does the export environment setting. This poses a bit of a problem if your proxy server is expecting both.

After a wee bit of research (about 20 mins as I get bored following the worldwide tangent and end up on IMDB for an hour before remembering what I was looking for in the first place) I stumbled upon this:

Ensure python is installed first, then

Download the latest version of NTLMAPS from

[http://sourceforge.net/projects/ntlmaps/](http://sourceforge.net/projects/ntlmaps/)

Yes, I know you can’t connect to the proxy server but if you change konqueror’s proxy settings:

open Konqueror,
SETTINGS
CONFIGURE KONQUEROR
scroll to PROXY
select Manually specify proxy setting - setup

and enter your proxy server settings you will be prompted to enter your username and password and this prompt WILL let you input it with the DOMAIN\USERNAME format.

Extract the contents of the downloaded file into a directory using your preferred extraction tool.

In a shell, or if you are already in one, CD into the directory and use VI or your favourite editor to modify server.cfg

Change:
LISTEN_PORT:5865 --swap for whatever local port you want

PARENT_PROXY_PORT:8080 --swap for your servers port

NT_DOMAIN:pdcl --swap for your domain name

USER:steve --swap for your username

PASSWORD:notgoingtotellyou --swap for your password

Save your changes and exit back to the prompt

Start the server with

pdcl-vaio3:/# python main.py

Open a new shell, keeping the previous one open, and export the following

pdcl-vaio3:/# export http_proxy=http://127.0.0.1:(local LISTEN_PORT that you set in server cfg)

pdcl-vaio3:/# export ftp_proxy=http://127.0.0.1:(local LISTEN_PORT that you set in server cfg)

Then start adept

pdcl-vaio3:/# Kdesu adept-manager

(kdesu if you are not running as root or don't have root access)

I’m fairly confident the same process will work in Ubuntu using synaptic, but either flavour can use apt-get etc in the shell.

* For browsing, open konqueror and change the settings under proxy server to local (127.0.0.1) and the port you set in server.cfg

There you go, Robert is your mother’s brother, updates through your company’s ISA proxy server.

*I recently tried this on openSuse but no matter what the setting, or combination of settings I couldn't get YaST to work on updates.

*It does, however, work on Fedora with yum, you just need to modify yum.conf and add the local proxy setting in there.

---


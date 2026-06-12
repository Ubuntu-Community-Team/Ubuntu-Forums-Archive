---
title: "FTP Vim Transaction"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by tufcamman on 2008-03-19
Hi,

I'm using VIM installed via the Add/Remove programs utility. I am trying to remotely access a file on an ftp server.

<code>
:o ftp://username@server.com//file.html
</code>

It prompts me for my password and I enter it and it proceeds to allow me to edit but nothing is present. It does give the message:

Illegal PORT command
ftp: bind: Address already in use

I have tried the same command under windows and it successfully opens my file, so I know that the syntax is correct. If anybody has any idea why I cannot use FTP vimming under Ubuntu that would be great. Any help would be greatly appreciated.

---

### Post by nixscripter on 2008-03-19
Try having vim use passive mode to get the file. Add this to the .vimrc file in your home directory: ```
let g:netrw_ftp_cmd="ftp -p"
``` (It's something I read on the internet, hopefully it will work.)

---

### Post by tufcamman on 2008-03-19
Thank you!  This solved the problem perfectly.

---


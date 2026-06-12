---
title: "Cannot reference images, css, js from cgi-bin"
date: 2010-04-19
forum: New to Ubuntu
---

### Post by rkad40 on 2010-04-19
I am trying to run Perl based CGI tools on a Linux server running Ubuntu.  My system admin is a bit of a novice at Linux configuration (though infinitely more knowledgeable than me).  

So, my admin set me up with a public cgi-bin directory and sure enough, I can execute CGI scripts from this directory.  

But there is one glaring problem ...

I can only execute scripts in this directory using the URL.  I cannot reference image files, CSS files, JavaScript files or even view HTML files in this or any sub-directory.  So in other words, if I want my CGI applications to look like Craig's List I'm golden.  But alas, this is not what I want.

My admin is really scratching his head on this one.  And unfortunately I'm not literate enough in Ubuntu to help him out.  It's not a permissions thing.  I know that much.  

Any words of wisdom from those that have some to spare?

---

### Post by patrickdc on 2010-04-19
this is normal behavior for a cgi directory. the server assumes all files in the cgi directory are scripts to be executed. what you can do is put the other files in a directory that is not the cgi directory or any of it's sub-directories. for example, pictures go in /pictures css goes in /styles js scripts go in /scripts and that cgi files go in /cgi-bin

---

### Post by rkad40 on 2010-04-19
Thank you Patrick.  This is actually one of the first things I tried.  I placed all reference content in a sub-directory of cgi-bin.  But unfortunately that didn't work.  Is there a setting that makes sub-directories viewable?  Shouldn't they be viewable by default?

Here is how the cgi-bin is configured ... 

My cgi-bin and executable script path looks like this:

[INDENT]/home/{user-id}/Public/cgi-bin/index.cgi
[/INDENT]
The URL that I run this script from looks like this:

[INDENT]http://{server.name}/cgi-bin/{user-id}/index.cgi
[/INDENT]
As I said, I tried putting CSS files in a sub-directory of the form:

[INDENT]/home/{user-id}/Public/cgi-bin/styles/default.css
[/INDENT]
But when I try to access the content here:

[INDENT]http://{server.name}/cgi-bin/{user-id}/styles/default.css
[/INDENT] 
I get a server error 500 file not found.

I even tried URL paths like http://{server.name}/~{user-id}/cgi-bin/styles/default.css but nothing I tried worked.  

Any ideas?

---

### Post by gmargo on 2010-04-20
I think patrickdc is saying that it is "normal" to have a structure with other directories parallel to the cgi-bin directory, not subdirectories.  (Although it is traditional to use $HOME/public_html/ for this, I'll follow your example of $HOME/Public/.)

```

$HOME/Public/                  <= top level directory
$HOME/Public/cgi-bin/          <= marked +ExecCGI
$HOME/Public/styles/           <= css files
$HOME/Public/scripts/          <= javascript?
$HOME/Public/html/             <= perhaps static web pages here?
$HOME/Public/images/           <= naughty pictures here!

```

---


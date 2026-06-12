---
title: "how to configure ldap password from squirrelmail"
date: 2011-07-30
forum: New to Ubuntu
---

### Post by nkdnkd on 2011-07-30
My org is running a squirrelmail 1.4.8 server with ldap for the user database. 
I wish to give the users a means to change their password in ldap database, from the mail web page (BTW - users are connecting to the mail server using web browser)

I checked out the  change_ldappass plugin. I did all the steps in the [link]("http://www.linuxmail.info/squirrelmail-ldap-change-password-howto/").
But finally when I try the command :-
    >    [COLOR=Blue]./ldap_chpasswd user[/COLOR]
       I get an error :-
            [COLOR=Red]: The wrong password was supplied or the SASL credentials could not be processed.    [/COLOR]
[COLOR=Black]I think I got the configuration step wrong. The link suggested setting up the [/COLOR] *ldap-chpasswd.cfg* file with value of the keys as  below. 
> $isActiveDirectory = 0; 
$hosts = "localhost";
 $domain = "acme.local";
 $searchBase = "dc=acme,dc=local"; 
$bindDN = "cn=manager,dc=acme,dc=local"; 
$bindPW = "secret";
 $userAttr = "uid"; 
My users have email id's like - [EMAIL="nishith@cc.gov"]nishith@cc.gov[/EMAIL]  and the administrator email is [EMAIL="admin@cc.gov"]admin@cc.gov[/EMAIL].
So I changed the settings as under :-
> $isActiveDirectory = 0;
$hosts = "localhost";
$domain = "cc.gov";
$searchBase = "dc=cc,dc=gov";
$bindDN = "cn=cc_admin,dc=cc,dc=gov";
$bindPW = "secret";
$userAttr = "uid";                       Did I set the variable values correctly ? or [COLOR=Navy]should I leave the cn=manager[/COLOR] ?

thanks in advance for any help / suggestions
nishith

---


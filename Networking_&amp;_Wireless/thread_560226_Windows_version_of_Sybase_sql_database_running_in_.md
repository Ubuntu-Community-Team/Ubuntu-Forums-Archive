---
title: "Windows version of Sybase sql database running in Wine"
date: 2007-09-26
forum: Networking &amp; Wireless
---

### Post by iraznatovic on 2007-09-26
I want to install a Sybase sqlanywhare 5.0.4 - a windows database on Ubuntu 7.0.4. Reason is for this is need for a faster system that is not bogged down by an antivirus or other stuff that would install on a Windows machine. I installed WINE and managed to run the server program (dbserve.exe). I also went to the Registry and added:

[COLOR=DarkSlateGray][HKEY_USERS\S-1-5-21-1960408961-484763869-839522115-500\Software\ODBC]

[HKEY_USERS\S-1-5-21-1960408961-484763869-839522115-500\Software\ODBC\ODBC.INI]

[HKEY_USERS\S-1-5-21-1960408961-484763869-839522115-500\Software\ODBC\ODBC.INI\Admin]
"Driver"="c:\\sqlany50\\win32\\wod50t.dll"
"Start"="c:\\sqlany50\\win32\\dbclient.exe"
"DatabaseName"="Admin"
"EngineName"="Server"
"AutoStop"="yes"
"DatabaseFile"="\\\\Server\\baza\\2007\\ADMIN.db"

[HKEY_USERS\S-1-5-21-1960408961-484763869-839522115-500\Software\ODBC\ODBC.INI\2007]
"Driver"="c:\\sqlany50\\win32\\wod50t.dll"
"Start"="c:\\sqlany50\\win32\\dbeng50.exe"
"DatabaseFile"="\\\\Server\\baza\\2007\\BS04.db"
"DatabaseName"="2007"
"AutoStop"="yes"
"EngineName"="Server"

[/COLOR]
As you can see all the files needed for the database to run are in the c:\sqlany50 folder (home\myname\.wine\drive_c\sqlany50) and the database files them selfs are in c:\baza (home\myname\.wine\drive_c\baza).

What else should I do to:
[LIST=1]
[*]Have the dbserv.exe connect to databases Admin & 2007
[*]Access these database files from a Windows client (do I need to share the folder c:\baza as it was needed until now on a win machine?)[/LIST]
Nothing that I looked on Interned answered my questions and I noticed that many people have tried this, while many say "in theory..."

---


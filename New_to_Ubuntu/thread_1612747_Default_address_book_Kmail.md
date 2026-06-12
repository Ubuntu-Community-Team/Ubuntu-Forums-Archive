---
title: "Default address book Kmail"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by liste on 2010-11-03
Hello everyone!

I recently installed Ubuntu for a friend, and I am trying to set up my email so that the address book (kaddressbook) will be my default address book.  I am using KMail because I was able to get it to look most similar to Outlook 2003 (3 column view).  I also installed kaddressbook, and put a link on my kMail toolbar.  I filled the address book with my contacts.

Here's the problem: When I create a new message, I want to be able to select an email address from my address book.  The "Select..." button brings up the "Select Recipient" dialogue box, but even when I choose "All" in the Address Book section, I do not get any of the contacts I put into kAddressBook.

Any help would be greatly appreciated as I have already spent several hours Googling for a solution.  I am willing to provide any and all information needed to help me resolve this issue.

Thank you!

**Edit:** I might add that the First time that I start kMail after starting the computer I get an "Akonadi Server Self-Test" dialogue box.  When I close the dialogue box, kMail also closes.  However, I can then open kMail without any problems, except that the contacts are missing when I try to write a new message.  I clicked "Copy report to clipboard" button, and here is the result.  I hope this helps:

Akonadi Server Self-Test Report
===============================

Test 1:  SUCCESS
--------

Database driver found.
Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system.

File content of '/home/owner/.config/akonadi/akonadiserverrc':
[QMYSQL]
Name=akonadi
Host=
Options="UNIX_SOCKET=/home/owner/.local/share/akonadi/db_misc/mysql.socket"
ServerPath=/usr/sbin/mysqld-akonadi
StartServer=true

[Debug]
Tracer=null


Test 2:  SUCCESS
--------

Akonadi is not running as root
Details: Akonadi is not running as a root/administrator user, which is the recommended setup for a secure system.

Test 3:  SUCCESS
--------

MySQL server found.
Details: You have currently configured Akonadi to use the MySQL server '/usr/sbin/mysqld-akonadi'.
Make sure you have the MySQL server installed, set the correct path and ensure you have the necessary read and execution rights on the server executable. The server executable is typically called 'mysqld'; its location varies depending on the distribution.

Test 4:  SUCCESS
--------

MySQL server is executable.
Details: MySQL server found: /usr/sbin/mysqld-akonadi  Ver 5.1.48-1ubuntu4 for debian-linux-gnu on i686 ((Ubuntu))


Test 5:  SUCCESS
--------

MySQL server log contains no errors.
Details: The MySQL server log file &apos;<a href='/home/owner/.local/share/akonadi/db_data/mysql.err'>/home/owner/.local/share/akonadi/db_data/mysql.err</a>&apos; does not contain any errors or warnings.

File content of '/home/owner/.local/share/akonadi/db_data/mysql.err':
101103 16:58:31 [Note] Plugin 'FEDERATED' is disabled.
101103 16:58:32  InnoDB: Started; log sequence number 0 734941
101103 16:58:33 [Note] /usr/sbin/mysqld-akonadi: ready for connections.
Version: '5.1.48-1ubuntu4'  socket: '/home/owner/.local/share/akonadi/db_misc/mysql.socket'  port: 0  (Ubuntu)


Test 6:  SUCCESS
--------

MySQL server default configuration found.
Details: The default configuration for the MySQL server was found and is readable at <a href='/etc/akonadi/mysql-global.conf'>/etc/akonadi/mysql-global.conf</a>.

File content of '/etc/akonadi/mysql-global.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris KÃ¶hntopp <kris@mysql.com>
#
[mysqld]
skip_grant_tables
skip_networking

# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
#sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
#sql_mode=strict_trans_tables

# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb
# case-insensitive table names, avoids trouble on windows
lower_case_table_names=1
character_set_server=utf8
collation_server=utf8_general_ci
table_cache=200
thread_cache_size=3
#log_bin=mysql-bin
#expire_logs_days=3
#sync_bin_log=0
# error log file name, relative to datadir
log_error=mysql.err
log_warnings=2
# log all queries, useful for debugging but generates an enormous amount of data
#log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
#log_slow_queries=mysql.slow
#long_query_time=1
# log queries not using indices, debug only, disable for production use
#log_queries_not_using_indexes=1
# maximum blob size
max_allowed_packet=32M
max_connections=256
# makes sense when having the same query multiple times
# makes no sense with prepared statements and/or transactions
query_cache_type=0
query_cache_size=0

innodb_file_per_table=1
innodb_log_buffer_size=1M
innodb_additional_mem_pool_size=1M
# messure database size and adjust
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");
innodb_buffer_pool_size=80M
# size of average write burst, keep Innob_log_waits small, keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)
innodb_log_file_size=64M
innodb_flush_log_at_trx_commit=2

# Do not drop the connection to the DB after 8 hours of inactivity
wait_timeout=1296000

[client]
default-character-set=utf8


Test 7:  SKIP
--------

MySQL server custom configuration not available.
Details: The custom configuration for the MySQL server was not found but is optional.

Test 8:  SUCCESS
--------

MySQL server configuration is usable.
Details: The MySQL server configuration was found at <a href='/home/owner/.local/share/akonadi/mysql.conf'>/home/owner/.local/share/akonadi/mysql.conf</a> and is readable.

File content of '/home/owner/.local/share/akonadi/mysql.conf':
#
# Global Akonadi MySQL server settings,
# These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf
#
# Based on advice by Kris KÃ¶hntopp <kris@mysql.com>
#
[mysqld]
skip_grant_tables
skip_networking

# strict query parsing/interpretation
# TODO: make Akonadi work with those settings enabled
#sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat
#sql_mode=strict_trans_tables

# use InnoDB for transactions and better crash recovery
default_storage_engine=innodb
# case-insensitive table names, avoids trouble on windows
lower_case_table_names=1
character_set_server=utf8
collation_server=utf8_general_ci
table_cache=200
thread_cache_size=3
#log_bin=mysql-bin
#expire_logs_days=3
#sync_bin_log=0
# error log file name, relative to datadir
log_error=mysql.err
log_warnings=2
# log all queries, useful for debugging but generates an enormous amount of data
#log=mysql.full
# log queries slower than n seconds, log file name relative to datadir (for debugging only)
#log_slow_queries=mysql.slow
#long_query_time=1
# log queries not using indices, debug only, disable for production use
#log_queries_not_using_indexes=1
# maximum blob size
max_allowed_packet=32M
max_connections=256
# makes sense when having the same query multiple times
# makes no sense with prepared statements and/or transactions
query_cache_type=0
query_cache_size=0

innodb_file_per_table=1
innodb_log_buffer_size=1M
innodb_additional_mem_pool_size=1M
# messure database size and adjust
# SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema");
innodb_buffer_pool_size=80M
# size of average write burst, keep Innob_log_waits small, keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables)
innodb_log_file_size=64M
innodb_flush_log_at_trx_commit=2

# Do not drop the connection to the DB after 8 hours of inactivity
wait_timeout=1296000

[client]
default-character-set=utf8


Test 9:  SUCCESS
--------

akonadictl found and usable
Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully.
Result:
Akonadi 1.4.0


Test 10:  SUCCESS
--------

Akonadi control process registered at D-Bus.
Details: The Akonadi control process is registered at D-Bus which typically indicates it is operational.

Test 11:  SUCCESS
--------

Akonadi server process registered at D-Bus.
Details: The Akonadi server process is registered at D-Bus which typically indicates it is operational.

Test 12:  ERROR
--------

Nepomuk search service not registered at D-Bus.
Details: The Nepomuk search service is not registered at D-Bus which typically means it was not started or encountered a fatal error during startup.

Test 13:  SKIP
--------

Protocol version check not possible.
Details: Without a connection to the server it is not possible to check if the protocol version meets the requirements.

Test 14:  SUCCESS
--------

Resource agents found.
Details: At least one resource agent has been found.

Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
gcalresource.desktop
googledataresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop
Directory listing of '/usr/share/akonadi/agents':
birthdaysresource.desktop
contactsresource.desktop
gcalresource.desktop
googledataresource.desktop
icalresource.desktop
imapresource.desktop
kabcresource.desktop
kcalresource.desktop
knutresource.desktop
kolabproxyresource.desktop
localbookmarksresource.desktop
maildirresource.desktop
maildispatcheragent.desktop
mboxresource.desktop
microblog.desktop
mtdummyresource.desktop
nepomukcalendarfeeder.desktop
nepomukcontactfeeder.desktop
nepomuktagresource.desktop
nntpresource.desktop
notesresource.desktop
pop3resource.desktop
vcarddirresource.desktop
vcardresource.desktop

Environment variable XDG_DATA_DIRS is set to '/usr/share/gnome:/usr/local/share/:/usr/share/'

Test 15:  SUCCESS
--------

No current Akonadi server error log found.
Details: The Akonadi server did not report any errors during its current startup.

Test 16:  SUCCESS
--------

No previous Akonadi server error log found.
Details: The Akonadi server did not report any errors during its previous startup.

Test 17:  SUCCESS
--------

No current Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its current startup.

Test 18:  SUCCESS
--------

No previous Akonadi control error log found.
Details: The Akonadi control process did not report any errors during its previous startup.

---

### Post by F for Fragging on 2010-11-06
Hi, I just encountered this bug as well in a fresh install of Kubuntu Maverick. I filed a bug here: [https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/671934](https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/671934) but the short story is that this – [http://userbase.kde.org/KAddressBook#Enabling_Resources](http://userbase.kde.org/KAddressBook#Enabling_Resources) – is probably the solution to your problem. I’m going to try that now.

---

### Post by liste on 2010-11-06
Hi F for Fragging!

Thank you so much for your response - it is Very much appreciated!  The only problem I have is that I cannot find "SystemSettings > Advanced tab > KDE Resources".  I think that it might be something specific to Kubuntu?

Does anyone know if there is a way to access that (even if it means installing something else) from Ubuntu 10.10?

---

### Post by F for Fragging on 2010-11-07
I had the same problem liste, I didn&#8217;t have an &#8216;Advanced&#8217; tab either.. If you follow [http://userbase.kde.org/KAddressBook#Enabling_Resources](http://userbase.kde.org/KAddressBook#Enabling_Resources) and scroll down a bit further, you read:

> In KDE SC 4.5 the path is slightly different although the process is the same. SystemSettings has been redesigned, so KDE resources is now found under Personal Information.

I had already become massively frustrated before I noticed that text. What I did then in KDE resources I don&#8217;t remember exactly, I probably created a new resource and then I somehow managed to get it to work. I can access the address book from KMail now.

I&#8217;m quite disappointed with Kubuntu/KDE though. I expected such a serious error to show up during testing, in the previous Kubuntu Akonadi had it&#8217;s problems too. I really hope the Akonadi developers can get their act together.

---

### Post by liste on 2010-11-08
OK.  Thank you, F for Fragging!  I finally figured out that I had to install KDE-systemsettings from Ubuntu Software Manager.  From there I was able to get almost everything working.  I'm still struggling to get the distribution lists working, though.  There must be something I have missed.  If you have any tips, I would be very grateful!

Again, many, many thanks for your input.  It is very much appreciated!

Liste

---

### Post by labonny on 2011-01-14
Liste: Like you, I had the same problem and installing & using the KDE System Settings as instructed to enable the address book fixed it except for my existing distribution lists (contact groups). I had created some contact groups in the address book before using KDE's System Settings. Afterwards, emailing the contact group did not work - it didn't use the email addresses in the contact group, but instead tried to use "name_of_contact_group@hostname". But creating a new contact group worked fine!

II found I had to edit my old contact groups again (I just added another email address to each one, then removed that email address) and then they worked.

Hope this helps someone.

---

### Post by glendeni on 2011-02-02
I also give thanks to F for Fragging.  On a Ubuntu 10.04 new install,  Kmail's "Tools" "Address book" would display "Personal Contacts" with names/addresses but when composing a new email they would not appear in the "Select recipients" popup.  Had to go to "System Settings" "Advanced Tab" "System Resources" and -- the key step -- "Add"  "Akonadi Address Books" and click "Use as standard".  I did beforehand check "System Settings" "Advanced Tab" "Desktop Search" to ensure  "Enable Neomuk Sematic Desktop" was checked.  Then in Kmail "Select recipients" popup I selected "akonadi-resource" in the "Address Book" window and the contact names/addresses appears!

---


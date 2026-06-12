---
title: "lost all Internet connection Control process died, committing suicide!"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by scrapmetal on 2010-09-08
**I have lost all Internet connection. Have no idea what to do.** HELP! :-(
*Any help getting it back greatly appreciated. Kubuntu 10.04*

Think it happened while using Kontact to set up a pop mail transfer (first time).
At the same session also imported and edited contacts (first time).
When looking at the File – Edit – etc drop down menus I clicked on some “configure ????” that I am guessing has selected the option of {use local server} which I do NOT have. This is just a guess.

The programs affected are – knetwork manager (does not run). Kpackagekit, synaptic package manager, Firefox, Konqueror etc.

Feeds, Journal and Popup Notes have not been used yet.

Contact is not working, a large red square with a white cross appears with
“Akonadi not operational.
Details....”

[I](FILE)
[SIZE=2]**Akonadiserver.error.old**[/SIZE]
(CONTENTS)
[SIZE=2]**Control process died, committing suicide!**[/SIZE]
(END CONTENTS)[/I]

[SIZE=2]
**Akonadi Server Self-Test Report**[/SIZE] =============================== Test 1: SUCCESS -------- Database driver found. Details: The QtSQL driver 'QMYSQL' is required by your current Akonadi server configuration and was found on your system. File content of '/home/vaughan/.config/akonadi/akonadiserverrc': [%General] Driver=QMYSQL SizeThreshold=4096 ExternalPayload=false [QMYSQL] Name=akonadi Host= User= Password= Options="UNIX_SOCKET=/home/vaughan/.local/share/akonadi/db_misc/mysql.socket" ServerPath=/usr/sbin/mysqld-akonadi StartServer=true [Debug] Tracer=null Test 2: SUCCESS -------- MySQL server found. Details: You currently have configured Akonadi to use the MySQL server '/usr/sbin/mysqld-akonadi'. Make sure you have the MySQL server installed, set the correct path and ensure you have the necessary read and execution rights on the server executable. The server executable is typically called 'mysqld', its locations varies depending on the distribution. Test 3: SUCCESS -------- MySQL server is executable. Details: MySQL server found: /usr/sbin/mysqld-akonadi Ver 5.1.41-3ubuntu11 for debian-linux-gnu on x86_64 ((Ubuntu)) Test 4: SUCCESS -------- MySQL server log contains no errors. Details: The MySQL server log file &apos;/home/vaughan/.local/share/akonadi/db_data/mysql.err&apos; does not contain any errors or warnings. File content of '/home/vaughan/.local/share/akonadi/db_data/mysql.err': 100905 22:38:59 [Note] Plugin 'FEDERATED' is disabled. 100905 22:38:59 InnoDB: Started; log sequence number 0 665816 100905 22:39:00 [Note] /usr/sbin/mysqld-akonadi: ready for connections. Version: '5.1.41-3ubuntu11-log' socket: '/home/vaughan/.local/share/akonadi/db_misc/mysql.socket' port: 0 (Ubuntu) Test 5: SUCCESS -------- MySQL server default configuration found. Details: The default configuration for the MySQL server was found and is readable at /etc/akonadi/mysql-global.conf. File content of '/etc/akonadi/mysql-global.conf': # # Global Akonadi MySQL server settings, # These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf # # Based on advice by Kris KÃƒÂ¶hntopp # [mysqld] skip_grant_tables skip_networking # strict query parsing/interpretation # TODO: make Akonadi work with those settings enabled #sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat #sql_mode=strict_trans_tables # use InnoDB for transactions and better crash recovery default_storage_engine=innodb # case-insensitive table names, avoids trouble on windows lower_case_table_names=1 character_set_server=latin1 collation_server=latin1_general_ci table_cache=200 thread_cache_size=3 log_bin=mysql-bin expire_logs_days=3 #sync_bin_log=0 # error log file name, relative to datadir log_error=mysql.err log_warnings=2 # log all queries, useful for debugging but generates an enormous amount of data #log=mysql.full # log queries slower than n seconds, log file name relative to datadir (for debugging only) #log_slow_queries=mysql.slow #long_query_time=1 # log queries not using indices, debug only, disable for production use #log_queries_not_using_indexes=1 # maximum blob size max_allowed_packet=32M max_connections=256 # makes sense when having the same query multiple times # makes no sense with prepared statements and/or transactions query_cache_type=0 query_cache_size=0 innodb_file_per_table=1 innodb_log_buffer_size=1M innodb_additional_mem_pool_size=1M # messure database size and adjust # SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema"); innodb_buffer_pool_size=80M # size of average write burst, keep Innob_log_waits small, keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables) innodb_log_file_size=64M innodb_flush_log_at_trx_commit=2 Test 6: SKIP -------- MySQL server custom configuration not available. Details: The custom configuration for the MySQL server was not found but is optional. Test 7: SUCCESS -------- MySQL server configuration is usable. Details: The MySQL server configuration was found at /home/vaughan/.local/share/akonadi/mysql.conf and is readable. File content of '/home/vaughan/.local/share/akonadi/mysql.conf': # # Global Akonadi MySQL server settings, # These settings can be adjusted using $HOME/.config/akonadi/mysql-local.conf # # Based on advice by Kris KÃƒÂ¶hntopp # [mysqld] skip_grant_tables skip_networking # strict query parsing/interpretation # TODO: make Akonadi work with those settings enabled #sql_mode=strict_trans_tables,strict_all_tables,strict_error_for_division_by_zero,no_auto_create_user,no_auto_value_on_zero,no_engine_substitution,no_zero_date,no_zero_in_date,only_full_group_by,pipes_as_concat #sql_mode=strict_trans_tables # use InnoDB for transactions and better crash recovery default_storage_engine=innodb # case-insensitive table names, avoids trouble on windows lower_case_table_names=1 character_set_server=latin1 collation_server=latin1_general_ci table_cache=200 thread_cache_size=3 log_bin=mysql-bin expire_logs_days=3 #sync_bin_log=0 # error log file name, relative to datadir log_error=mysql.err log_warnings=2 # log all queries, useful for debugging but generates an enormous amount of data #log=mysql.full # log queries slower than n seconds, log file name relative to datadir (for debugging only) #log_slow_queries=mysql.slow #long_query_time=1 # log queries not using indices, debug only, disable for production use #log_queries_not_using_indexes=1 # maximum blob size max_allowed_packet=32M max_connections=256 # makes sense when having the same query multiple times # makes no sense with prepared statements and/or transactions query_cache_type=0 query_cache_size=0 innodb_file_per_table=1 innodb_log_buffer_size=1M innodb_additional_mem_pool_size=1M # messure database size and adjust # SELECT sum(data_length) as bla, sum(index_length) as blub FROM information_schema.tables WHERE table_schema not in ("mysql", "information_schema"); innodb_buffer_pool_size=80M # size of average write burst, keep Innob_log_waits small, keep Innodb_buffer_pool_wait_free small (see show global status like "inno%", show global variables) innodb_log_file_size=64M innodb_flush_log_at_trx_commit=2 Test 8: SUCCESS -------- akonadictl found and usable Details: The program '/usr/bin/akonadictl' to control the Akonadi server was found and could be executed successfully. Result: Akonadi 1.3.1 Test 9: SUCCESS -------- Akonadi control process registered at D-Bus. Details: The Akonadi control process is registered at D-Bus which typically indicates it is operational. Test 10: SUCCESS -------- Akonadi server process registered at D-Bus. Details: The Akonadi server process is registered at D-Bus which typically indicates it is operational. Test 11: SUCCESS -------- Nepomuk search service registered at D-Bus. Details: The Nepomuk search service is registered at D-Bus which typically indicates it is operational. Test 12: SUCCESS -------- Nepomuk search service uses an appropriate backend. Details: The Nepomuk search service uses one of the recommended backends. Test 13: SUCCESS -------- Server protocol version is recent enough. Details: The server Protocol version is 23, which equal or newer than the required version 23. Test 14: ERROR -------- No resource agents found. Details: No resource agents have been found, Akonadi is not usable without at least one. This usually means that no resource agents are installed or that there is a setup problem. The following paths have been searched: '/usr/share/akonadi/agents /usr/share/akonadi/agents'. The XDG_DATA_DIRS environment variable is set to '/usr/share:/usr/share:/usr/local/share', make sure this includes all paths where Akonadi agents are installed to. Directory listing of '/usr/share/akonadi/agents': birthdaysresource.desktop contactsresource.desktop icalresource.desktop imapresource.desktop kabcresource.desktop kcalresource.desktop knutresource.desktop kolabproxyresource.desktop localbookmarksresource.desktop maildirresource.desktop maildispatcheragent.desktop mboxresource.desktop microblog.desktop mtdummyresource.desktop nepomukcalendarfeeder.desktop nepomukcontactfeeder.desktop nepomuktagresource.desktop nntpresource.desktop notesresource.desktop pop3resource.desktop vcarddirresource.desktop vcardresource.desktop Directory listing of '/usr/share/akonadi/agents': birthdaysresource.desktop contactsresource.desktop icalresource.desktop imapresource.desktop kabcresource.desktop kcalresource.desktop knutresource.desktop kolabproxyresource.desktop localbookmarksresource.desktop maildirresource.desktop maildispatcheragent.desktop mboxresource.desktop microblog.desktop mtdummyresource.desktop nepomukcalendarfeeder.desktop nepomukcontactfeeder.desktop nepomuktagresource.desktop nntpresource.desktop notesresource.desktop pop3resource.desktop vcarddirresource.desktop vcardresource.desktop Environment variable XDG_DATA_DIRS is set to '/usr/share:/usr/share:/usr/local/share' Test 15: SUCCESS -------- No current Akonadi server error log found. Details: The Akonadi server did not report any errors during its current startup. Test 16: ERROR -------- Previous Akonadi server error log found. Details: The Akonadi server did report error during its previous startup into /home/vaughan/.local/share/akonadi/akonadiserver.error.old. File content of '/home/vaughan/.local/share/akonadi/akonadiserver.error.old': Control process died, committing suicide! Test 17: SUCCESS -------- No current Akonadi control error log found. Details: The Akonadi control process did not report any errors during its current startup. Test 18: SUCCESS -------- No previous Akonadi control error log found. Details: The Akonadi control process did not report any errors during its previous startup.

---

### Post by undecim on 2010-09-08
From what I've been able to find about this error, it seems to be a fluke. Have your tried logging out and then back in since this problem appeared?

---

### Post by scrapmetal on 2010-09-08
Not only logged out but shut down.
Have been trying all I could find.
3 days worth.

Can I remove certain programs and reload from
cd / usb drive to solve the problem?

By using mouse pointer over conection.
Wired conection reports - 
Unmanaged

Right click =
Network Manager Disabled

Thanks for reply - I'm drowning here, not waving ):P

---

### Post by anubhavrocks on 2010-09-08
Can you create a new user, and login using this new user.If things are allright with this new user then most probably something is wrong with your local settings.

---

### Post by scrapmetal on 2010-09-08
Sorry did **not work**.
[SIZE=2]**thanks**[/SIZE]:popcorn:

---

### Post by anubhavrocks on 2010-09-08
Can you try this:
[http://ubuntuforums.org/showthread.php?t=25557](http://ubuntuforums.org/showthread.php?t=25557)

---

### Post by scrapmetal on 2010-09-09
**Thanks Anubhav,**
Sorry so long to reply. Sleep Break.
Thanks for the link.
First Command...netstsat -nr in terminal confirmed
no network entries.
Will try a manual (terminal) rebuild of network connection.

Once again **THANKS** :-)
Will record process, and if successful will post results here.

**ANYONE.** Any ideas of why, or what happened?, if it will happen again appreciated.

NOTE:
Have posted the original posting on KDE site, so hopefully they are aware of it.

---

### Post by jtarin on 2010-09-09
I've had some problems with Akonadi server and KDE before. It runs in conjunction with that Desktop search application....can't think of the name at the moment, but I remember I didn't need it or want it when I ran Slackware so I disabled it. Can't remember how. Do a Google. It's tied in with a lot of other things and I think removal wasn't the option. Just keep the Akonadi server from starting at boot.

---

### Post by scrapmetal on 2010-09-09
**Note that as a beginner, ie: not a command line native user the following comments are by a newbie and treat as such.**:KS

After much web searching I have come to the conclusion that the maintenance processes involved to use these programs effectively out ways their usefulness.:KS

Without knowing it I have, (can affect server system)

Hibernated with said program/s open, (a number of times without manually stopping and starting SQL base server)
Imported a Vcard database, (may have incorrect character entries in it)
Ignored first warning screen, (other programs were still running ok - web access etc)
Used POP mail from Gmail to mail program inappropriately.

Current conclusion.
Run Thunderbird Instead):P

**[SIZE="2"]Tanks to all that helped.;)[/SIZE]**
Am going to re load as I have /home partition separate and backed up.
**Any comments on Ubuntu 10.04 with VirtualBox, would like to include Mythbuntu as well on same machine.**

---


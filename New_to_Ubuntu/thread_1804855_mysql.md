---
title: "mysql"
date: 2011-07-15
forum: New to Ubuntu
---

### Post by maryhigginsrice on 2011-07-15
Hi everyone.  I have been trying to get Mythtv to work in Ubuntu 11.04 and haven't had any success.  I continue to receive an error message: Could not connect to the master backend sever.  Is it running?Is the ip address set for it in the mythtv-setup correct?  I ip address is correct and I have purge all the files and reinstalled mythtv and nothing seems to work.  I looked at the backend logs,but i do not understand them.  Here is a copy of the backend logs  Any assistance will be appreciated.  mary

2011-07-15 05:27:49.374 Closing DB connection named 'DBManager0'
2011-07-15 05:27:49.423 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:27:49.480 Current locale EN_US
2011-07-15 05:27:49.534 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-15 05:27:49.598 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-15 05:27:49.649 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-15 05:27:49.708 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-15 05:27:49.757 MythBackend: Starting up as the master server.
2011-07-15 05:27:49.816 New DB connection, total: 2
2011-07-15 05:27:49.868 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:27:49.928 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:27:49.980 ChannelBase(1) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 05:27:50.037 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:27:50.183 ChannelBase(2) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 05:27:50.370 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:27:50.669 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:50.986 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:51.086 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:51.186 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:51.286 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:51.386 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:51.486 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:51.586 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:51.686 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:51.786 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:51.887 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:51.987 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:52.087 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:52.187 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:52.287 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:52.387 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:52.487 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:52.587 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:52.688 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:52.788 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:52.838 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2011-07-15 05:27:52.893 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-15 05:27:52.950 New DB scheduler connection
2011-07-15 05:27:53.005 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:27:53.061 Scheduler, Warning: Listings source 'analog' is defined, but is not attached to a card input.
2011-07-15 05:27:53.116 Scheduler, Warning: Listings source 'digital' is defined, but is not attached to a card input.
2011-07-15 05:27:53.172 Scheduler, Error: No channel sources defined in the database
2011-07-15 05:27:53.304 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 05:27:53.383 Using runtime prefix = /usr
2011-07-15 05:27:53.428 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 05:27:53.473 Empty LocalHostName.
2011-07-15 05:27:53.517 Using localhost value of deanie53
2011-07-15 05:27:53.569 New DB connection, total: 1
2011-07-15 05:27:53.610 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:27:53.669 Closing DB connection named 'DBManager0'
2011-07-15 05:27:53.707 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:27:53.752 Current locale EN_US
2011-07-15 05:27:53.796 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-15 05:27:53.848 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-15 05:27:53.888 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-15 05:27:53.934 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-15 05:27:53.974 MythBackend: Starting up as the master server.
2011-07-15 05:27:54.022 New DB connection, total: 2
2011-07-15 05:27:54.063 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:27:54.111 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:27:54.153 ChannelBase(1) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 05:27:54.198 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:27:54.242 ChannelBase(2) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 05:27:54.287 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:27:54.331 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:54.425 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:54.514 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:54.603 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:54.692 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:54.781 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:54.870 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:54.959 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:55.048 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:55.137 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:55.226 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:55.315 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:55.404 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:55.493 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:55.582 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:55.671 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:55.760 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:55.849 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:55.938 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:56.505 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:27:56.755 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2011-07-15 05:27:57.077 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-15 05:27:57.222 New DB scheduler connection
2011-07-15 05:27:57.278 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:27:57.335 Scheduler, Warning: Listings source 'analog' is defined, but is not attached to a card input.
2011-07-15 05:27:57.390 Scheduler, Warning: Listings source 'digital' is defined, but is not attached to a card input.
2011-07-15 05:27:57.723 Scheduler, Error: No channel sources defined in the database
2011-07-15 05:29:37.063 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 05:29:37.144 Using runtime prefix = /usr
2011-07-15 05:29:37.201 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 05:29:37.257 Empty LocalHostName.
2011-07-15 05:29:37.312 Using localhost value of deanie53
2011-07-15 05:29:37.400 New DB connection, total: 1
2011-07-15 05:29:37.459 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:37.535 Closing DB connection named 'DBManager0'
2011-07-15 05:29:37.592 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:37.648 Current locale EN_US
2011-07-15 05:29:37.702 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-15 05:29:37.766 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-15 05:29:37.817 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-15 05:29:37.874 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-15 05:29:37.926 MythBackend: Starting up as the master server.
2011-07-15 05:29:37.984 New DB connection, total: 2
2011-07-15 05:29:38.037 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:38.096 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:29:38.149 ChannelBase(1) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 05:29:38.205 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:29:38.364 ChannelBase(2) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 05:29:38.427 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:29:38.482 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:38.587 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:38.687 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:38.787 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:38.887 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:38.988 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:39.088 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:39.188 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:39.288 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:39.388 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:39.477 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:39.577 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:39.666 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:39.755 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:39.849 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:39.944 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:40.056 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:40.167 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:40.268 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:40.357 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:40.419 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2011-07-15 05:29:40.508 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-15 05:29:40.586 New DB scheduler connection
2011-07-15 05:29:40.664 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:40.742 Scheduler, Warning: Listings source 'analog' is defined, but is not attached to a card input.
2011-07-15 05:29:40.820 Scheduler, Warning: Listings source 'digital' is defined, but is not attached to a card input.
2011-07-15 05:29:40.897 Scheduler, Error: No channel sources defined in the database
2011-07-15 05:29:41.017 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 05:29:41.098 Using runtime prefix = /usr
2011-07-15 05:29:41.186 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 05:29:41.232 Empty LocalHostName.
2011-07-15 05:29:41.275 Using localhost value of deanie53
2011-07-15 05:29:41.331 New DB connection, total: 1
2011-07-15 05:29:41.403 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:41.584 Closing DB connection named 'DBManager0'
2011-07-15 05:29:41.767 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:41.934 Current locale EN_US
2011-07-15 05:29:42.122 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-15 05:29:42.299 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-15 05:29:42.359 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-15 05:29:42.417 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-15 05:29:42.501 MythBackend: Starting up as the master server.
2011-07-15 05:29:42.848 New DB connection, total: 2
2011-07-15 05:29:42.912 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:42.971 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:29:43.024 ChannelBase(1) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 05:29:43.081 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:29:43.220 ChannelBase(2) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 05:29:43.269 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:29:43.324 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:43.429 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:43.529 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:43.629 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:43.730 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:43.830 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:44.041 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:44.341 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:44.586 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:44.686 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:44.786 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:44.886 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:44.986 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:45.086 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:45.186 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:45.286 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:45.387 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:45.487 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:45.587 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:45.687 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:45.737 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2011-07-15 05:29:45.793 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-15 05:29:45.849 New DB scheduler connection
2011-07-15 05:29:45.904 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:45.960 Scheduler, Warning: Listings source 'analog' is defined, but is not attached to a card input.
2011-07-15 05:29:46.016 Scheduler, Warning: Listings source 'digital' is defined, but is not attached to a card input.
2011-07-15 05:29:46.326 Scheduler, Error: No channel sources defined in the database
2011-07-15 05:29:46.699 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 05:29:46.960 Using runtime prefix = /usr
2011-07-15 05:29:47.005 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 05:29:47.050 Empty LocalHostName.
2011-07-15 05:29:47.216 Using localhost value of deanie53
2011-07-15 05:29:47.513 New DB connection, total: 1
2011-07-15 05:29:47.753 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:47.801 Closing DB connection named 'DBManager0'
2011-07-15 05:29:47.839 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:47.886 Current locale EN_US
2011-07-15 05:29:47.928 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-15 05:29:47.987 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-15 05:29:48.046 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-15 05:29:48.094 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-15 05:29:48.341 MythBackend: Starting up as the master server.
2011-07-15 05:29:48.388 New DB connection, total: 2
2011-07-15 05:29:48.429 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:48.477 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:29:48.530 ChannelBase(1) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 05:29:48.575 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:29:48.619 ChannelBase(2) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 05:29:48.664 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 05:29:48.707 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:48.802 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:48.891 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:48.980 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:49.069 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:49.158 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:49.247 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:49.336 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:49.425 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:49.514 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:49.603 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:49.692 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:49.781 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:49.870 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:49.959 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:50.048 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:50.137 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:50.237 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:50.337 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:50.437 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 05:29:50.487 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2011-07-15 05:29:50.544 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-15 05:29:50.601 New DB scheduler connection
2011-07-15 05:29:50.656 Connected to database 'mythconverg' at host: localhost
2011-07-15 05:29:50.712 Scheduler, Warning: Listings source 'analog' is defined, but is not attached to a card input.
2011-07-15 05:29:50.767 Scheduler, Warning: Listings source 'digital' is defined, but is not attached to a card input.
2011-07-15 05:29:50.823 Scheduler, Error: No channel sources defined in the database
2011-07-15 06:03:38.734 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 06:03:38.999 Using runtime prefix = /usr
2011-07-15 06:03:39.312 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 06:03:39.531 Empty LocalHostName.
2011-07-15 06:03:39.612 Using localhost value of deanie53
2011-07-15 06:03:40.064 New DB connection, total: 1
2011-07-15 06:03:40.265 Unable to connect to database!
2011-07-15 06:03:40.324 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2011-07-15 06:03:42.495 UPnPautoconf() - No UPnP backends found
2011-07-15 06:03:42.618 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-07-15 06:03:43.130 Deleting UPnP client...
2011-07-15 06:03:43.544 Failed to init MythContext.
2011-07-15 06:03:43.797 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 06:03:44.043 Using runtime prefix = /usr
2011-07-15 06:03:44.432 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 06:03:44.578 Empty LocalHostName.
2011-07-15 06:03:44.644 Using localhost value of deanie53
2011-07-15 06:03:44.696 New DB connection, total: 1
2011-07-15 06:03:44.860 Unable to connect to database!
2011-07-15 06:03:45.034 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2011-07-15 06:03:47.149 UPnPautoconf() - No UPnP backends found
2011-07-15 06:03:47.358 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-07-15 06:03:47.648 Deleting UPnP client...
2011-07-15 06:03:48.146 Failed to init MythContext.
2011-07-15 06:03:48.278 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 06:03:48.315 Using runtime prefix = /usr
2011-07-15 06:03:48.371 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 06:03:48.416 Empty LocalHostName.
2011-07-15 06:03:48.460 Using localhost value of deanie53
2011-07-15 06:03:48.512 New DB connection, total: 1
2011-07-15 06:03:48.553 Unable to connect to database!
2011-07-15 06:03:48.594 Driver error was [1/1045]:
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)

................................................................................
2011-07-15 06:03:50.687 UPnPautoconf() - No UPnP backends found
2011-07-15 06:03:50.740 No UPnP backends found

No UPnP backends found

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
2011-07-15 06:03:51.007 Deleting UPnP client...
2011-07-15 06:03:51.683 Failed to init MythContext.
2011-07-15 06:55:22.618 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 06:55:22.698 Using runtime prefix = /usr
2011-07-15 06:55:22.754 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 06:55:22.799 Empty LocalHostName.
2011-07-15 06:55:22.843 Using localhost value of deanie53
2011-07-15 06:55:22.905 New DB connection, total: 1
2011-07-15 06:55:23.007 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:23.052 Closing DB connection named 'DBManager0'
2011-07-15 06:55:23.090 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:23.136 Current locale EN_US
2011-07-15 06:55:23.179 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-15 06:55:23.233 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-15 06:55:23.285 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-15 06:55:23.344 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-15 06:55:23.391 MythBackend: Starting up as the master server.
2011-07-15 06:55:23.453 New DB connection, total: 2
2011-07-15 06:55:23.536 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:23.622 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 06:55:23.681 ChannelBase(1) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 06:55:23.727 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 06:55:26.531 ChannelBase(2) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 06:55:26.629 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 06:55:26.727 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:26.843 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:26.954 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:27.066 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:27.155 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:27.244 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:27.355 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:27.444 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:27.533 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:27.635 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:27.724 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:27.813 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:27.902 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:27.991 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:28.080 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:28.169 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:28.258 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:28.347 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:28.436 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:28.525 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:28.564 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2011-07-15 06:55:28.609 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-15 06:55:28.654 New DB scheduler connection
2011-07-15 06:55:28.698 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:28.755 Scheduler, Warning: Listings source 'analog' is defined, but is not attached to a card input.
2011-07-15 06:55:28.810 Scheduler, Warning: Listings source 'digital' is defined, but is not attached to a card input.
2011-07-15 06:55:28.865 Scheduler, Error: No channel sources defined in the database
2011-07-15 06:55:28.984 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 06:55:29.043 Using runtime prefix = /usr
2011-07-15 06:55:29.099 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 06:55:29.144 Empty LocalHostName.
2011-07-15 06:55:29.188 Using localhost value of deanie53
2011-07-15 06:55:29.240 New DB connection, total: 1
2011-07-15 06:55:29.281 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:29.351 Closing DB connection named 'DBManager0'
2011-07-15 06:55:29.390 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:29.447 Current locale EN_US
2011-07-15 06:55:29.511 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-15 06:55:29.583 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-15 06:55:29.641 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-15 06:55:29.698 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-15 06:55:29.735 MythBackend: Starting up as the master server.
2011-07-15 06:55:29.795 New DB connection, total: 2
2011-07-15 06:55:29.835 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:29.895 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 06:55:29.936 ChannelBase(1) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 06:55:29.981 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 06:55:30.108 ChannelBase(2) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 06:55:30.159 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 06:55:30.202 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:30.297 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:30.397 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:30.497 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:30.597 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:30.687 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:30.776 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:30.865 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:30.954 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.043 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.132 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.221 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.310 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.399 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.488 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.577 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.666 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.755 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.844 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.933 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:31.972 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2011-07-15 06:55:32.017 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-15 06:55:32.063 New DB scheduler connection
2011-07-15 06:55:32.107 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:32.252 Scheduler, Warning: Listings source 'analog' is defined, but is not attached to a card input.
2011-07-15 06:55:32.529 Scheduler, Warning: Listings source 'digital' is defined, but is not attached to a card input.
2011-07-15 06:55:32.773 Scheduler, Error: No channel sources defined in the database
2011-07-15 06:55:32.893 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 06:55:32.953 Using runtime prefix = /usr
2011-07-15 06:55:32.997 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 06:55:33.043 Empty LocalHostName.
2011-07-15 06:55:33.086 Using localhost value of deanie53
2011-07-15 06:55:33.138 New DB connection, total: 1
2011-07-15 06:55:33.180 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:33.226 Closing DB connection named 'DBManager0'
2011-07-15 06:55:33.266 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:33.311 Current locale EN_US
2011-07-15 06:55:33.354 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-15 06:55:33.408 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-15 06:55:33.459 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-15 06:55:33.505 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-15 06:55:33.544 MythBackend: Starting up as the master server.
2011-07-15 06:55:33.592 New DB connection, total: 2
2011-07-15 06:55:33.633 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:33.682 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 06:55:33.723 ChannelBase(1) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 06:55:33.769 TVRec(2) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 06:55:33.906 ChannelBase(2) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?
2011-07-15 06:55:33.958 TVRec(3) Error: Problem finding starting channel, setting to default of '3'.
2011-07-15 06:55:34.012 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:34.128 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:34.228 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:34.317 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:34.418 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:34.518 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:34.618 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:34.707 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:34.796 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:34.885 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:34.974 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:35.063 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:35.163 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:35.264 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:35.353 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:35.453 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:35.553 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:35.642 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:35.731 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:35.820 DVBChan(3:/dev/dvb/adapter0/frontend0) Warning: Opening DVB frontend device failed.
            eno: Device or resource busy (16)
2011-07-15 06:55:35.859 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: Failed to open DVB frontend device due to fatal error or too many attempts.
2011-07-15 06:55:35.915 MythBackend, Warning: No valid capture cards are defined in the database.
2011-07-15 06:55:35.960 New DB scheduler connection
2011-07-15 06:55:36.005 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 06:55:36.049 Scheduler, Warning: Listings source 'analog' is defined, but is not attached to a card input.
2011-07-15 06:55:36.093 Scheduler, Warning: Listings source 'digital' is defined, but is not attached to a card input.
2011-07-15 06:55:36.138 Scheduler, Error: No channel sources defined in the database
2011-07-15 07:29:19.834 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 07:29:19.898 Using runtime prefix = /usr
2011-07-15 07:29:19.943 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 07:29:19.988 Empty LocalHostName.
2011-07-15 07:29:20.033 Using localhost value of deanie53
2011-07-15 07:29:20.094 New DB connection, total: 1
2011-07-15 07:29:20.150 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 07:29:20.197 Closing DB connection named 'DBManager0'
2011-07-15 07:29:20.245 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 07:29:20.290 Current locale EN_US
2011-07-15 07:29:20.333 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-15 07:29:20.388 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-15 07:29:20.445 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-15 07:29:20.498 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-15 07:29:20.546 MythBackend: Starting up as the master server.
2011-07-15 07:29:20.594 New DB connection, total: 2
2011-07-15 07:29:20.657 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 07:29:20.707 New DB connection, total: 3
2011-07-15 07:29:20.757 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 07:29:20.841 format_to_mode() does not recognize V4L1
2011-07-15 07:29:21.003 DVBChan(2:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): CheckChannel failed.
            Please verify the channel in the 'mythtv-setup' Channel Editor.
2011-07-15 07:29:21.058 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): CheckChannel failed.
            Please verify the channel in the 'mythtv-setup' Channel Editor.
2011-07-15 07:29:21.103 New DB scheduler connection
2011-07-15 07:29:21.146 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 07:29:21.224 Main::Registering HttpStatus Extension
2011-07-15 07:29:21.280 Enabled verbose msgs:  important general
2011-07-15 07:29:21.375 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-15 07:29:24.212 Reschedule requested for id -1.
2011-07-15 07:29:24.358 Scheduled 0 items in 0.1 = 0.08 match + 0.06 place
2011-07-15 07:29:24.409 Seem to be woken up by USER
2011-07-15 07:30:41.225 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-15 07:40:48.199 MainServer::ANN Monitor
2011-07-15 07:40:48.259 adding: deanie53 as a client (events: 0)
2011-07-15 07:40:48.304 MainServer::ANN Monitor
2011-07-15 07:40:48.359 adding: deanie53 as a client (events: 1)
2011-07-15 07:40:48.407 Reschedule requested for id -1.
2011-07-15 07:40:48.514 Scheduled 0 items in 0.1 = 0.04 match + 0.06 place
2011-07-15 07:51:03.701 mythbackend version: fixes/0.24 [v0.24-243-g9ba3ece] [www.mythtv.org](www.mythtv.org)
2011-07-15 07:51:03.769 Using runtime prefix = /usr
2011-07-15 07:51:03.825 Using configuration directory = /home/mythtv/.mythtv
2011-07-15 07:51:03.871 Empty LocalHostName.
2011-07-15 07:51:03.914 Using localhost value of deanie53
2011-07-15 07:51:03.989 New DB connection, total: 1
2011-07-15 07:51:04.041 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 07:51:04.088 Closing DB connection named 'DBManager0'
2011-07-15 07:51:04.138 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 07:51:04.183 Current locale EN_US
2011-07-15 07:51:04.226 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-07-15 07:51:04.283 Current MythTV Schema Version (DBSchemaVer): 1264
2011-07-15 07:51:04.334 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-07-15 07:51:04.380 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2011-07-15 07:51:04.428 MythBackend: Starting up as the master server.
2011-07-15 07:51:04.478 New DB connection, total: 2
2011-07-15 07:51:04.517 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 07:51:04.567 New DB connection, total: 3
2011-07-15 07:51:04.606 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 07:51:04.704 format_to_mode() does not recognize V4L1
2011-07-15 07:51:04.875 DVBChan(2:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): CheckChannel failed.
            Please verify the channel in the 'mythtv-setup' Channel Editor.
2011-07-15 07:51:04.940 DVBChan(3:/dev/dvb/adapter0/frontend0) Error: SetChannelByString(Please add): CheckChannel failed.
            Please verify the channel in the 'mythtv-setup' Channel Editor.
2011-07-15 07:51:04.984 New DB scheduler connection
2011-07-15 07:51:05.028 Connected to database 'mythconverg' at host: 127.0.0.1
2011-07-15 07:51:05.077 Main::Registering HttpStatus Extension
2011-07-15 07:51:05.117 Enabled verbose msgs:  important general
2011-07-15 07:51:05.167 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-07-15 07:51:08.081 Reschedule requested for id -1.
2011-07-15 07:51:08.196 Scheduled 0 items in 0.1 = 0.05 match + 0.06 place
2011-07-15 07:51:08.247 Seem to be woken up by USER
2011-07-15 07:52:25.079 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min

---

### Post by alphacrucis2 on 2011-07-15
I don't have a clue what most of that stuff means, especially never having used mythtv myself but one thing stands out like a sore thumb - a number of occurrences of:

```
QMYSQL: Unable to connect
Database error was:
Access denied for user 'mythtv'@'localhost' (using password: YES)
```

I presume you have to set up a usercode and password for mythtv to be able to use mysql.

---

### Post by &lt;mike&gt; on 2011-08-06
...in which case, it looks like you may need to check the values in  /etc/mythtv/mysql.txt to ensure they match /etc/mythtv/config.xml

You should be able to log into the database from the console by typing

```
mysql -u mythtv -p`cat /etc/mythtv/mysql.txt | grep DBPassword | cut -d= -f2` mythconverg
```

(which is an automated way of running

```
mysql -umythtv -p mythconverg
```

without being prompted for a password.)


But looking over your log, there are too many 'Connected to database 'mythconverg' and host: localhost' lines to make this a likely cause.

The ones which look more likely to me are:
```

Could not get inputs for the capturecard.
Perhaps you have forgotten to bind video
sources to your card's inputs?

Scheduler, Warning: Listings source 'analog' is defined, but is not attached to a card input.
```

Check in the backend setup that you have bound your card's inputs to the sources you've set up. This is under 'Input Connections' in the backend setup program.

---


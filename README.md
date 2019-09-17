#Please manually run these commands:
#echo ip_addr
./ssh_nopasswd root@ip_addr

#/dev/vdb -> entire ext4 /dev/vdb1
./remote_format_disk root@ip_addr vdb

./install_mongo_ubuntu root@ip_addr

#start mongo
./start_mongo_replica root@ip_addr1 ip_addr1 0 /vdb

./start_mongo_replica root@ip_addr2 ip_addr2 1 /vdb

./start_mongo_replica root@ip_addr3 ip_addr3 2 /vdb

#init mongo to make replica work
#for user specific config, diy
#ip_addr1 ->primary
#ip_addr3 ->decay one day
./init_mongo_replica_config user(root) ip_addr1 ip_addr2 ip_addr3

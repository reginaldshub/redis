Redis:
--------------------------------------------------------------------------------------
Redis is a datastructure and combination of NoSQL and memCache
It is fast so widely used
we can enable the persistance property to store to the memory

> First step is to install the redis from official website
redis-cli --version   mine is 4.0.9

> To start the redis server /etc/init.d/redis-server start

> To stop the redis server /etc/init.d/redis-server stop

> To restart the redis server /etc/init.d/redis-server restart

> To open the cli  redis-cli

> Test the cli by following
	* ping  prints out PONG
	* quit to quit from cli
	* set foo 100
	* get foo
	* incr foo (increments value of foo)
	* decr foo (decrements value of foo)
	* exists foo (returns 1 if exist else 0)
	* del foo (deletes and returns 1 is success else 0)
	* flushall (clears everything)
	* expire foo 10 (foo gets deleted after 10 seconds)
	* ttl foo (gives the remaining time to expire)
	* setex foo 10 "HEY" (setting value with expiration)
	* persist foo (even if key expires the value is retained)
	* mset foo "hello" bar "world!!!!!" (multiple key value setting)
	* append foo world (appending the value)
	* rename foo regi (renamed foo key with regi. value will be same. foo becomes nil)

	
	> Working with Lists:

* lpush people regi
* lpush people anthony
* lpush people tony 
* rpush people "reginald anthony"
* linsert people before anthony kabali (adds kabali before anthony) 
* linsert people after tony robo (adds robo after tony) 
* lrange people 0 -1 (displays everything)
* llen people (length of list)
* lpop people (pop's first element from left)
* rpop people (pop's first element from right)

 	> Working with Sets: SADD
* sadd cars "ford"
* sadd cars "maruthi"
* sadd cars "suzuki" 
* sismember cars ford (returns 1 if ford is present in cars set)
* smembers cars (dispays contents of cars set)
* scard cars (cardinality of set cars)
* smove cars newcars maruti (moves maruthi to new cars set)
* srem cars suzuki (removes suzuki from cars set) 

	> working with sorted sets: ZADD
* zadd users 1997 "reginald"
* zadd users 1996 "anthony"
* zadd users 1989 "brother"
* zadd users 1990 "sister"
* zrank users "brother" (returns 0 as the lowest value)
* zrank users "reginald" (returns 3 as the highest value)
* zrange users 0 -1 (display contents of users set)
* zincrby users 1 "anthony" (increments anthony by 1 => 1997)

	> Working with hashes: HSET
* hset user:regi name reginald
* hset user:regi email reginald@gmail.com
* hget user:regi name
* hgetall user:regi (everything is displayed)
* hmset user:regi name "reginald anthony" email "regianth@gmail.com" age "22"
* hkeys user:regi (gives all keys "name" "email" "age")
* hvals user:regi (gives all values "reginald anthony" "regianth@gmail.com" "22")
* hincrby user:regi age 1 (increment by 1)
* hdel user:regi age


	> PERSISTENCE
Snapshot and AOF
* save 60 1000 (every 60 seconds if at least 1000 keys changed)

check the file dump.rdb in admin:///var/lib/redis
 
to update config file for AOF
open redis.conf from admin:///etc/redis
change appendonly to yes from no

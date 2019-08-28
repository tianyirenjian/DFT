### Common ###

dbsize

```
127.0.0.1:6379> dbsize
(integer) 22
```

keys pattern

```
127.0.0.1:6379> keys *
 1) "n"
 2) "k"
 3) "d"
 4) "world"
 5) "e"
 6) "i"
 7) "num"
 8) "g"
 9) "a"
10) "key"
11) "hellonx"
12) "hello"
13) "h"
14) "j"
15) "l"
16) "f"
17) "b"
18) "m"
19) "chinese"
20) "uuu"
21) "letters"
22) "c"
```

del key [key ...]

```
127.0.0.1:6379> del l m n
(integer) 3
```

type key

```
127.0.0.1:6379> type hello
string
```

object encoding [arguments [arguments ...]]

```
127.0.0.1:6379> object encoding hello
"raw"
```

### String ###

set key value [ex seconds] [px milliseconds] [nx|xx]

```
127.0.0.1:6379> set hello world
OK
127.0.0.1:6379> get hello
"world"
```

setex key seconds value

```
127.0.0.1:6379> setex helloex 10 world
OK
127.0.0.1:6379> ttl helloex
(integer) 7 (should be 10.)
```

setnx key value

```
127.0.0.1:6379> exists hello
(integer) 1
127.0.0.1:6379> setnx hello world
(integer) 0
127.0.0.1:6379> setnx hellonx world
(integer) 1
```

get key

```
127.0.0.1:6379> get hello
"world"
127.0.0.1:6379> get hellonx
"world"
127.0.0.1:6379> get not_exist
(nil)
```

mset key value [key value ...] | mget key [key ...]

```
127.0.0.1:6379> mset a 1 b 2 c 3 d 4 e 5 f 6 g 7
OK
127.0.0.1:6379> mget a b c d e f g
1) "1"
2) "2"
3) "3"
4) "4"
5) "5"
6) "6"
7) "7"
```

incr key | decr key | incrby key | decrby key | incrby float

```
127.0.0.1:6379> incr num
(integer) 1
127.0.0.1:6379> decr num
(integer) 0
127.0.0.1:6379> incrby num 20
(integer) 20
127.0.0.1:6379> incrby num -2
(integer) 18
127.0.0.1:6379> incrbyfloat num 2.31
"20.31"
127.0.0.1:6379> incrbyfloat num -0.54
"19.77"
```

append key value

```
127.0.0.1:6379> get hello
"world"
127.0.0.1:6379> append hello " redis"
(integer) 11
127.0.0.1:6379> get hello
"world redis"
```

strlen key

```
127.0.0.1:6379> strlen hello
(integer) 11
127.0.0.1:6379> strlen not_exist
(integer) 0
```

getset key value

```
127.0.0.1:6379> getset hello "hello redis"
"world redis"
127.0.0.1:6379> get hello
"hello redis"
```

setrange key offeset value

```
127.0.0.1:6379> get hello
"hello redis"
127.0.0.1:6379> setrange hello 5 ---
(integer) 11
127.0.0.1:6379> get hello
"hello---dis"
```

getrange key start end

```
127.0.0.1:6379> getrange hello 0 -1
"hello---dis"
127.0.0.1:6379> getrange hello 2 8
"llo---d"
```

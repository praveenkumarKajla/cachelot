# cachelot
A mutex based in-memory cache system JS

Installation

`npm i cachelot --save`

Usage

```typescript

    const defaultExpiration: number = 5*60 * 1000; // 5 minutes
    const cleanupInterval: number = 1*60*1000 // 1minute
    const cache = cachelot.New(defaultExpiration, cleanupInterval)

    // with locking
    await cache.Set("key", "value", defaultExpiration + defaultExpiration)

    // without locking
    cache.set("key", "value", defaultExpiration + defaultExpiration)

     // with locking
    const [object, found] =  await cache.Get("key")
    const [object, expiration, found] =  await cache.GetWithExpiration("key")
    
    // without locking
     const [object, found] = cache.get("key")



    // on delete or every time janitor clean up the expired items this function would run
     cache.OnEvicted = (key, value) => {
         console.log(`Item expired & evicted => ${key} : ${value.toString()}`)
     }


```




## Inspired from

[go-cache](https://github.com/patrickmn/go-cache)
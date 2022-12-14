
# An efficient Priority Queue in Rust

The algorithm was implemented using a [Heap data-structure](https://www.geeksforgeeks.org/binary-heap/).

# Usage example

### Popping least priority element

```rust
use epqueue::{PQueue, Priority};

fn main() {
    let mut asc_priority_queue = PQueue::new(Priority::Asc);

    asc_priority_queue.insert(9);
    asc_priority_queue.insert(1);
    asc_priority_queue.insert(7);
    asc_priority_queue.insert(4);

    println!("queue representation as heap:\n{:?}", asc_priority_queue);

    match asc_priority_queue.pop() {
        Some(top) => println!("pop operation: {}", top),
        None => println!("cannot pop from empty queue")
    };
}
```

Running:

```sh
$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.00s
     Running `target/debug/epqueue`

queue representation as heap:
 - 1, pos: 1
     - 4, pos: 2
         - 9, pos: 4
     - 7, pos: 3
pop operation: 1
```

### Iterator Trait

The priority queue implements the `Iterator` trait, so you can iterate over the elements.

```rust
use epqueue::{PQueue, Priority};

fn main() {
    let mut asc_priority_queue = PQueue::new(Priority::Asc);

    asc_priority_queue.insert(9);
    asc_priority_queue.insert(1);
    asc_priority_queue.insert(7);
    asc_priority_queue.insert(4);

    for top in asc_priority_queue {
        print!("{} ", top);
    }

    println!("\nQueue is empty, consumed all queue elements", );
}
```

Output:

```
1 4 7 9 
Queue is empty, consumed all queue elements
```

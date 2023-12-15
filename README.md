# springStudy
## 인프런 스프링 프레임워크 입문 강의 복습 (백기선님) (section 1)


스프링이 뭔데?

스프링 프레임워크(이하, 스프링)를 사용한 예제 코드를 보며 스프링의 주요 철학과 기능을
빠르게 학습합니다.

## IoC소개
### Inversion of Control
제어가 뒤바꼈다고? 뭔 소리야?
“내가 쓸 놈은 내가 만들어 쓸께...” (일반적인 의존성에 대한 제어권)

    class OwnerController {
      private OwnerRepository repository = new OwnerRepository();
    }


“내가 쓸 놈은 이 놈인데... 누군가 알아서 주겠지...” (IoC)
● 내가 쓸 놈의 타입만 맞으면 어떤거든 상관없지 뭐.. .
● 그래야 내 코드 테스트 하기도 편하지.

    class OwnerController {
        private OwnerRepository repo;
        public OwnerController(OwnerRepository repo) {
            this.repo = repo;
        }
    // repo를 사용합니다.
    }
    class OwnerControllerTest {
        @Test
        public void create() {
            OwnerRepository repo = new OwnerRepository();
            OwnerController controller = new OwnerController(repo);
        }
    }




## IoC (Inversion of Control) 컨테이너
IoC (Inversion of Control) 컨테이너

ApplicationContext (BeanFactory)
빈(bean)을 만들고 엮어주며 제공해준다.
빈 설정
● 이름 또는 ID
● 타입
● 스코프
아이러니하게도 컨테이너를 직접 쓸 일은 많지 않다.




## 빈
빈 (Bean)

스프링 IoC 컨테이너가 관리하는 객체

어떻게 등록하지?
● Component Scanning
  ○ @Component
    ■ @Repository
    ■ @Service
    ■ @Controller

● 또는 직접 일일히 XML이나 자바 설정 파일에 등록
어떻게 꺼내쓰지?
● @Autowired 또는 @Inject
● 또는 ApplicationContext에서 getBean()으로 직접 꺼내거나

특징
● 오로지 “빈"들만 의존성 주입을 해줍니다.



## 의존성 주입
의존성 주입 (Dependency Injection)

필요한 의존성을 어떻게 받아올 것인가..

@Autowired / @Inject를 어디에 붙일까?
● 생성자
● 필드
● Setter

---

#include <iostream>
#include <string>
#include <cstdlib>

using namespace std;

/* ---------- Conponent (Đồ uống) ---------- */

class DoUong {
public:
    virtual ~DoUong() {};
    virtual string MoTa() = 0;      // Lấy tên đồ uống
    virtual int GiaTien() = 0;      // Lấy giá tiền
};

/* ---------- Concrete Conponents (Các loại đồ uống) ---------- */

// Sữa tươi
class SuaTuoi : public DoUong {
public:
    string MoTa() override { return "Sua Tuoi"; }
    int GiaTien() override { return 12000; }
};

// Trà sữa
class TraSua : public DoUong {
public:
    string MoTa() override { return "Tra Sua"; }
    int GiaTien() override { return 20000; }
};

// Tàu hũ
class TauHu : public DoUong {
public:
    string MoTa() override { return "Tau Hu"; }
    int GiaTien() override { return 10000; }
};

/* ---------- Base Decorator (Topping) ---------- */

class Topping : public DoUong {
protected:
    DoUong* doUong;

public:
    Topping(DoUong* m) : doUong(m) {}
    ~Topping() { delete doUong; }
};

/* ---------- Concrete Decorators (Các loại topping) ---------- */

// Trân châu trắng
class TranChauTrang : public Topping {
public:
    TranChauTrang(DoUong* m) : Topping(m) {}
    string MoTa() override { return doUong->MoTa() + " + Tran Chau Trang"; }
    int GiaTien() override { return doUong->GiaTien() + 3000; }
};

// Trân châu đường đen
class TranChauDuongDen : public Topping {
public:
    TranChauDuongDen(DoUong* m) : Topping(m) {}
    string MoTa() override { return doUong->MoTa() + " + Tran Chau Duong Den"; }
    int GiaTien() override { return doUong->GiaTien() + 8000; }
};

// Kem trứng
class KemTrung : public Topping {
public:
    KemTrung(DoUong* m) : Topping(m) {}
    string MoTa() override { return doUong->MoTa() + " + Kem Trung"; }
    int GiaTien() override { return doUong->GiaTien() + 10000; }
};

// Sương sáo
class SuongSao : public Topping {
public:
    SuongSao(DoUong* m) : Topping(m) {}
    string MoTa() override { return doUong->MoTa() + " + Suong Sao"; }
    int GiaTien() override { return doUong->GiaTien() + 5000; }
};

int main() {
    DoUong* lyNuoc = nullptr;

    int base;
    while (1) {
        system("cls");

        // Menu đồ uống
        cout << "==================================================="   << "\n";
        cout << "                MENU CHON DO UONG                  "   << "\n";
        cout << "==================================================="   << "\n";
        cout << "[1] Sua Tuoi (12k)"                                    << "\n";
        cout << "[2] Tra Sua (20k)"                                     << "\n";
        cout << "[3] Tau Hu (10k)"                                      << "\n";
        cout << "---------------------------------------------------"   << "\n";
        cout << "Nhap lua chon: "; cin >> base;

        // Đặt món
        if (base == 1) { lyNuoc = new SuaTuoi();    break; }
        if (base == 2) { lyNuoc = new TraSua();     break; }
        if (base == 3) { lyNuoc = new TauHu();      break; }

        // Thông báo chọn lại khi nhập sai
        cout << "Lua chon khong hop le, nhan phim bat ki de chon lai."  << "\n";
        system("pause");
    }

    int deco;
    while (1) {
        system("cls");

        // Menu topping
        cout << "==================================================="   << "\n";
        cout << "             MENU MIX TOPPING TU CHON              "   << "\n";
        cout << "==================================================="   << "\n";
        cout << "Do uong hien tai: " << lyNuoc->MoTa()                  << "\n";
        cout << "Gia tam tinh: " << lyNuoc->GiaTien() << " VND"         << "\n";
        cout << "---------------------------------------------------"   << "\n";
        cout << "[1] Tran Chau Trang (3k)"                              << "\n";
        cout << "[2] Tran Chau Duong Den (8k)"                          << "\n";
        cout << "[3] Kem Trung (10k)"                                   << "\n";
        cout << "[4] Suong Sao (5k)"                                    << "\n";
        cout << "[0] THANH TOAN"                                        << "\n";
        cout << "---------------------------------------------------"   << "\n";
        cout << "Nhap lua chon: "; cin >> deco;

        // Thêm topping
        if (deco == 1) { lyNuoc = new TranChauTrang(lyNuoc);    continue; }
        if (deco == 2) { lyNuoc = new TranChauDuongDen(lyNuoc); continue; }
        if (deco == 3) { lyNuoc = new KemTrung(lyNuoc);         continue; }
        if (deco == 4) { lyNuoc = new SuongSao(lyNuoc);         continue; }

        // Thanh toán
        if (deco == 0) break;

        // Thông báo chọn lại khi nhập sai
        cout << "Lua chon khong hop le, nhan phim bat ki de chon lai."  << "\n";
        system("pause");
    }

    system("cls"); 

    // Hóa đơn
    cout << "---------------------------------------------------"       << "\n";
    cout << "                 HOA DON THANH TOAN                "       << "\n";
    cout << "---------------------------------------------------"       << "\n";
    cout << "Do uong da chon: " << lyNuoc->MoTa()                       << "\n";
    cout << "Tong cong: " << lyNuoc->GiaTien() << " VND"                << "\n";
    cout << "---------------------------------------------------"       << "\n";

    delete lyNuoc;

    return 0;
}
